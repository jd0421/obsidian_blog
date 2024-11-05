---
{"dg-publish":true,"permalink":"/000-public/index/","tags":["gardenEntry"],"created":"2024-11-05T20:24:18.792+09:00"}
---


# 홈페이지에 오신 것을 환영합니다!

<div class="sidebar">
  <h2>파일 탐색기</h2>
  <ul id="file-explorer">
    <!-- 자바스크립트로 파일 목록을 생성 -->
  </ul>
</div>

<div class="content">
  <h1>홈페이지 제목</h1>
  <p>여기에는 사이트의 간단한 소개문을 작성합니다. 아래에는 사이트의 주요 섹션으로 가는 링크를 추가합니다.</p>

  <section id="hero">
    <h2>여기에 주요 소개 문구를 추가하세요</h2>
    <p>사이트에 대한 설명을 간략히 적어 방문자에게 관심을 유도합니다.</p>
  </section>
</div>

<style>
  /* CSS 스타일링 */
  body {
    display: flex;
    margin: 0;
    font-family: Arial, sans-serif;
  }

  .sidebar {
    width: 250px;
    background-color: #f4f4f4;
    padding: 1em;
    height: 100vh;
    position: fixed;
    overflow-y: auto;
    border-right: 1px solid #ddd;
  }

  .content {
    margin-left: 250px;
    padding: 1em;
    width: calc(100% - 250px);
  }

  #file-explorer {
    list-style: none;
    padding: 0;
  }

  #file-explorer li a {
    color: #333;
    text-decoration: none;
    padding: 0.5em;
    display: block;
  }

  #file-explorer li a:hover {
    background-color: #ddd;
  }
</style>

<script>
  // JavaScript로 파일 목록 추가
  const files = [
    { title: "홈", path: "/" },
    { title: "블로그", path: "/blog" },
    { title: "소개", path: "/about" },
    { title: "연락처", path: "/contact" }
  ];

  const fileExplorer = document.getElementById('file-explorer');
  files.forEach(file => {
    const listItem = document.createElement('li');
    const link = document.createElement('a');
    link.href = file.path;
    link.textContent = file.title;
    listItem.appendChild(link);
    fileExplorer.appendChild(listItem);
  });
</script>


[[000_public/untitled/medium\|medium]]
[[000_public/untitled/velog\|velog]]
