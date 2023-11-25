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
