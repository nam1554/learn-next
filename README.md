## Next.js App Router Course - Starter

This is the starter template for the Next.js App Router Course. It contains the starting code for the dashboard application.

For more information, see the [course curriculum](https://nextjs.org/learn) on the Next.js Website.

## Chapter 1

npx create-next-app@latest nextjs-dashboard --use-npm --example "https://github.com/vercel/next-learn/tree/main/dashboard/starter-example"

npm i
npm run dev

## Chapter 2

CSS Styling

Tailwind and CSS modules 2가지 방법
home.module.css

Using the clsx library to toggle class names

## Chapter 3

Optimizing Fonts and Images

Cumulative Layout Shift

빌드시 글꼴을 다운로드
추가 네트워크 요청이 없도록 다른 정적 자산과 함께 글꼴 파일을 호스팅합니다.

The &lt;Image&gt; Component

이미지가 로드될 때 자동으로 레이아웃 이동을 방지합니다.
뷰포트가 더 작은 장치에 큰 이미지가 전달되는 것을 방지하기 위해 이미지 크기를 조정합니다.
기본적으로 Lazy loading images(이미지가 뷰포트에 들어갈 때 로드됨)
브라우저가 지원하는 경우 WebP 및 AVIF와 같은 최신 형식으로 이미지를 제공합니다.

치수와 웹 글꼴이 없는 이미지는 레이아웃 변경의 일반적인 원인입니다.

## Chapter 4

Creating Layouts and Pages

레이아웃 파일은 애플리케이션의 모든 페이지에서 사용할 수 있는 공유 레이아웃을 만드는 가장 좋은 방법입니다.

## Chapter 5

Navigating Between Pages

The &lt;Link&gt; component

Automatic code-splitting and prefetching

또한 프로덕션 환경에서 &lt;Link&gt; 구성 요소가 브라우저의 뷰포트에 나타날 때마다 Next.js는 백그라운드에서 연결된 경로에 대한 코드를 자동으로 미리 가져옵니다.

Pattern: Showing active links
'use client'; usePathname()

## Chapter 6

Setting Up Your Database

vercel 에서 postgres 데이터베이스 생성
env 파일 수정
npm i @vercel/postgres 설치
script "seed" 추가

What is 'seeding' in the context of databases?
-> Populating the database with an initial set of data

## Chapter 7

Fetching Data

1. The data requests are unintentionally blocking each other, creating a request waterfall.
2. By default, Next.js prerenders routes to improve performance, this is called Static Rendering. So if your data changes, it won't be reflected in your dashboard.

What are request waterfalls?

Parallel data fetching

you can use the Promise.all() or Promise.allSettled() functions to initiate all promises at the same time

## Chapter 8

Static and Dynamic Rendering

What is Static Rendering?

1. Faster Websites
2. Reduced Server Load
3. SEO

What is Dynamic Rendering?

1. Real-Time Data
2. User-Specific Content
3. Request Time Information

## Chapter 9

Streaming

What is streaming?

What is one advantage of streaming?
-> 청크가 병렬로 렌더링되어 전체 로드 시간이 단축됩니다.

loading.tsx &lt;DashboardSkeleton /&gt;

Fixing the loading skeleton bug with route groups
route grorp 사용하여 loading 화면을 대시보드에만 적용

Streaming a component

Suspense 이용 -> 컴포넌트 단위로 fallback 컴포넌트 노출

Grouping components

Deciding where to place your Suspense boundaries

1. 페이지가 스트리밍될 때 사용자가 페이지를 경험하기를 원하는 방식입니다.
2. 어떤 콘텐츠에 우선순위를 두고 싶은지.
3. 구성요소가 데이터 가져오기에 의존하는 경우.

4. loading.tsx에서 했던 것처럼 전체 페이지를 스트리밍할 수 있지만 구성 요소 중 하나의 데이터 가져오기 속도가 느린 경우 로드 시간이 더 길어질 수 있습니다.
5. 모든 구성 요소를 개별적으로 스트리밍할 수 있지만 UI가 준비되면 화면에 갑자기 나타날 수 있습니다.(UI popping)
6. 페이지 섹션을 스트리밍하여 staggered effect(시차 효과)를 만들 수도 있습니다. 하지만 래퍼 구성 요소를 만들어야 합니다.

일반적으로 Suspense 및 데이터 가져오기 작업 시 모범 사례로 간주되는 것은 무엇입니까?
-> data fetches(데이터 가져오기)를 필요한 구성요소로 이동

## Chapter 10

Partial Prerendering (Optional)

Combining Static and Dynamic Content

현재 경로 내에서 동적 함수(예: noStore(), cookie() 등)를 호출하면 전체 경로가 동적이 됩니다.

What is Partial Prerendering?

부분 사전 렌더링은 일부 부분을 동적으로 유지하면서 정적 로딩 shell을 사용하여 경로를 렌더링할 수 있는 실험적 기능입니다. 즉, 경로의 동적 부분을 분리할 수 있습니다.

How does Partial Prerendering work?

부분 사전 렌더링은 React의 Concurrent API를 활용하고 Suspense를 사용하여 일부 조건이 충족될 때까지(예: 데이터 로드) 애플리케이션의 렌더링 부분을 연기합니다.

fallback는 다른 정적 콘텐츠와 함께 초기 정적 파일에 포함됩니다. 빌드 시(또는 유효성 재검사 중에) 경로의 정적 부분이 사전 렌더링되고 나머지 부분은 사용자가 경로를 요청할 때까지 연기됩니다.

## Chapter 11

Adding Search and Pagination

Why use URL search params?

1. 북마크 가능 및 공유 가능 URL: 검색 매개변수가 URL에 있으므로 사용자는 향후 참조 또는 공유를 위해 검색 쿼리 및 필터를 포함하여 애플리케이션의 현재 상태를 북마크할 수 있습니다.
2. 서버 측 렌더링 및 초기 로드: URL 매개변수를 서버에서 직접 사용하여 초기 상태를 렌더링할 수 있으므로 서버 렌더링을 더 쉽게 처리할 수 있습니다.
3. 분석 및 추적: URL에 직접 검색어와 필터가 있으면 추가 클라이언트 측 논리 없이도 사용자 행동을 더 쉽게 추적할 수 있습니다.

Adding the search functionality

useSearchParams
usePathname
useRouter

When to use the useSearchParams() hook vs. the searchParams prop?

&lt;Search&gt; is a Client Component, so you used the useSearchParams() hook to access the params from the client.
&lt;Table&gt; is a Server Component that fetches its own data, so you can pass the searchParams prop from the page to the component.

npm i use-debounce

Adding pagination

## Chapter 12

Mutating Data

What are Server Actions?

React Server Actions를 사용하면 서버에서 직접 비동기 코드를 실행할 수 있습니다.
데이터를 변경하기 위해 API 엔드포인트를 생성할 필요가 없습니다.
대신, 서버에서 실행되고 클라이언트 또는 서버 구성 요소에서 호출될 수 있는 비동기 함수를 작성합니다.

Using forms with Server Actions

React에서는 &lt;form&gt; 요소의 action 속성을 사용하여 액션을 호출할 수 있습니다.
작업은 캡처된 데이터가 포함된 기본 FormData 개체를 자동으로 수신합니다.

Next.js with Server Actions

An advantage of invoking a Server Action within a Server Component is progressive enhancement - forms work even if JavaScript is disabled on the client.

#### Creating an invoice

1. Create a new route and form
2. Create a Server Action

By adding the 'use server', you mark all the exported functions within the file as server functions.
These server functions can then be imported into Client and Server components, making them extremely versatile.

You can also write Server Actions directly inside Server Components by adding "use server" inside the action. But for this course, we'll keep them all organized in a separate file.

HTML에서는 action 속성에 URL을 전달합니다.
이 URL은 양식 데이터를 제출해야 하는 대상(일반적으로 API 엔드포인트)입니다.

그러나 React에서 action 속성은 특별한 prop으로 간주됩니다. 즉, React가 그 위에 액션을 호출할 수 있도록 빌드된다는 의미입니다.
배후에서 서버 작업은 POST API 엔드포인트를 생성합니다. 이것이 바로 서버 작업을 사용할 때 API 엔드포인트를 수동으로 생성할 필요가 없는 이유입니다.

3. Extract the data from formData

Object.fromEntries(formData.entries());

4. Validate and prepare the data

zod

5. Inserting the data into your database

6. Revalidate and redirect

#### Updating an invoice

1. Create a new dynamic route segment with the invoice id.

Dynamic Route Segments

2. Read the invoice id from the page params.
3. Fetch the specific invoice from your database.

UUIDs vs. Auto-incrementing Keys

4. Pre-populate the form with the invoice data.
5. Update the invoice data in your database.

#### Deleting an invoice

이 장에서는 서버 작업을 사용하여 데이터를 변경하는 방법을 배웠습니다.
또한 revalidatePath API를 사용하여 Next.js 캐시의 유효성을 다시 검사하고 사용자를 새 페이지로 리디렉션하도록 리디렉션하는 방법도 배웠습니다.

## Chapter 13

Handling Errors

error.tsx needs to be a Client Component.

It accepts two props:
error: This object is an instance of JavaScript's native Error object.
reset: This is a function to reset the error boundary. When executed, the function will try to re-render the route segment.

notFound는 error.tsx보다 우선순위가 높으므로 더 구체적인 오류를 처리하고 싶을 때 이에 접근할 수 있습니다

[Error Handling](https://nextjs.org/docs/app/building-your-application/routing/error-handling)
[error.js API Reference](https://nextjs.org/docs/app/api-reference/file-conventions/error)
[notFound() API Reference](https://nextjs.org/docs/app/api-reference/functions/not-found)
[not-found.js API Reference](https://nextjs.org/docs/app/api-reference/file-conventions/not-found)

## Chapter 14

Improving Accessibility

What is accessibility?

form의 접근성을 개선하기 위해 이미 세 가지 작업을 수행하고 있습니다.

1. Semantic HTML
2. Labelling
3. Focus Outline

### Form validation

#### Client-Side validation

input prop required

#### Server-Side validation

useFormState
