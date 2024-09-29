---
layout: default
title: Home
---

# 최근 게시글

<ul>
  {% for post in paginator.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small class="post-date" data-date="{{ post.date | date: '%Y-%m-%dT%H:%M:%S%z' }}"></small>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>

<div>
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path }}">이전 페이지</a>
  {% endif %}
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path }}">다음 페이지</a>
  {% endif %}
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // 모든 날짜 요소를 선택
    const dates = document.querySelectorAll('.post-date');

    dates.forEach(function(dateElement) {
      // HTML에서 ISO 형식으로 저장된 날짜 읽기
      const isoDate = dateElement.getAttribute('data-date');

      // 로컬 시간으로 변환
      const date = new Date(isoDate);

      // 사용자의 로케일에 맞게 날짜 포맷 적용
      const formattedDate = new Intl.DateTimeFormat(navigator.language, {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      }).format(date);

      // 날짜를 포맷한 값으로 설정
      dateElement.textContent = formattedDate;
    });
  });
</script>
