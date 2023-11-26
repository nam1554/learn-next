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

loading.tsx &lt;DashboardSkeleton /&gt;;

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
