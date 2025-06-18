<script>
  // @ts-nocheck

  import { onMount } from 'svelte';
  import { BanknoteIcon, IdCardIcon, LandmarkIcon } from '@lucide/svelte';

  const CONTACT_URL = import.meta.env.VITE_CONTACT_URL;

  // Reactive language state, default to Korean
  let lang = 'ko';

  let scrolled = false;

  onMount(() => {
    document.documentElement.classList.remove('dark');
    document.documentElement.classList.add('light');

    const savedLang = localStorage.getItem('lang');
    if (savedLang) {
      lang = savedLang;
    }

    const onScroll = () => {
      scrolled = window.scrollY > 10;
    };
    window.addEventListener('scroll', onScroll);
    onScroll();
    return () => window.removeEventListener('scroll', onScroll);
  });

  // Language data for English and Korean
  const translations = {
    en: {
      title: 'KDC',
      home: 'Home',
      about: 'About',
      team: 'Team',
      services: 'Services',
      contact: 'Contact',
      heroTitle: 'Korea Digital Currency',
      heroSubtitle: 'Building the foundation of a trusted digital society',
      getInTouch: 'Get in Touch',
      aboutTitle: 'Korea Digital Currency',
      aboutText1:
        'From digital identity to local currency, we securely connect public services and everyday life.',
      aboutText2:
        'In particular, the core development team played a central role in the creation of COOV, the official government COVID-19 vaccination certification app. Introduced in 2021, COOV was the world’s first tamper-proof vaccine authentication system based on DID technology and was used by more than a quarter of the Korean population.',
      aboutText3:
        'Korea Digital Currency builds trust through technology and bridges the future with that trust.',
      aboutTeam: 'Meet the Team',
      aboutTeamText1:
        'The Korea Digital Currency team is composed of experts from major Korean tech companies such as Samsung Electronics, Samsung SDS, Coupang, and LINE. Our team members have demonstrated proven capabilities through a variety of projects, including digital transformation, development of DID (Decentralized Identity) platforms, and large-scale infrastructure implementation.',
      aboutTeamText2:
        'Notably, our core development team played a pivotal role in the official government COVID‑19 vaccine authentication app, COOV. It was the world’s first DID-based tamper-proof vaccine verification system, used by over 25% of the population.',
      aboutTeamText3:
        'This experience demonstrates Korea Digital Currency’s capability to design and implement efficient, integrity-driven solutions across digital identity, local currency, and public authentication infrastructures.',
      servicesTitle: 'Our Key Services',
      servicesText1:
        'Korea Digital Currency provides infrastructure that proves and leverages data authenticity.',
      servicesText2:
        'We add trust and transparency to a wide range of public and private services.',
      service1Title: 'Digital Identity',
      service1Text:
        'We provide a digital identity system suitable for public and private institutions, offering strong privacy protection and seamless inter-institutional authentication capabilities.',
      service2Title: 'Local Currency',
      service2Text:
        'We build digital local currency platforms optimized for municipalities, covering issuance, circulation, user experience, and settlement.',
      service3Title: 'Public Authentication Infrastructure',
      service3Text:
        'We enable secure storage and verification of data integrity for public services across administration, education, healthcare, and more.',
      contactTitle: 'Contact Us',
      formSuccess: 'Thank you! We will get back to you soon.',
      nameLabel: 'Name',
      emailLabel: 'Email',
      messageLabel: 'Message',
      sendButton: 'Send',
      email: 'contact@kdccy.com',
      footer: '© 2025 Korea Digital Currency'
    },
    ko: {
      title: 'KDC',
      home: '홈',
      about: '소개',
      team: '팀',
      services: '서비스',
      contact: '연락처',
      heroTitle: '한국디지털커런시',
      heroSubtitle: '신뢰할 수 있는 디지털 사회의 기반을 만듭니다',
      getInTouch: '문의하기',
      aboutTitle: '한국디지털커런시',
      aboutText1: '디지털 신분증부터 지역화폐까지, 공공과 일상을 안전하게 연결합니다.',
      aboutText2:
        '한국디지털커런시는 데이터의 신뢰성과 위·변조 방지 기술을 기반으로 디지털 신분증, 지역화폐, 공공 인증 시스템 등 다양한 솔루션을 제공합니다. 한국디지털커런시는 단순한 기술 개발을 넘어, 실제 사용 가능한 시스템을 구축하고, 사회에 필요한 서비스를 구현합니다.',
      aboutText3: '한국디지털커런시는 기술로 신뢰를 만들고, 그 신뢰로 미래를 연결합니다.',
      aboutTeam: '팀 소개',
      aboutTeamText1:
        '한국디지털커런시 팀은 삼성전자, 삼성SDS, 쿠팡, 라인 등 국내 주요 기술 기업 출신의 전문가들로 구성되어 있습니다. 팀원들은 디지털 전환, DID(분산신원인증) 기반 플랫폼 개발, 대규모 인프라 구축 등 다양한 프로젝트를 통해 검증된 역량을 갖추고 있습니다.',
      aboutTeamText2:
        '특히, 핵심 개발진은 정부 공식 COVID-19 백신 접종 인증 앱인 COOV 개발에서 중심적인 역할을 맡았습니다. COOV는 2021년, 세계 최초로 DID 기반의 위변조 방지 백신 인증 시스템으로 도입되었으며, 전 국민의 4분의 1 이상이 사용했습니다.',
      aboutTeamText3:
        '이러한 경험은 한국디지털커런시가 디지털 신분증, 지역화폐, 공공 인증 인프라 등 다양한 영역에서 신뢰와 무결성을 핵심 가치로 삼아, 현장 중심의 효율적인 솔루션 설계와 구현 역량을 보유하고 있음을 입증합니다.',
      servicesTitle: '대표 서비스',
      servicesText1:
        '한국디지털커런시는 데이터의 진위를 증명하고 활용할 수 있는 인프라를 제공합니다.',
      servicesText2: '다양한 공공 및 민간 서비스에 신뢰와 투명성을 더합니다.',
      service1Title: '디지털 신분증',
      service1Text:
        '민간 및 공공기관에 적용 가능한 디지털 신분증 시스템을 제공합니다. 개인정보 보호는 물론, 기관 간 인증 연동도 고려된 인프라입니다.',
      service2Title: '지역 화폐',
      service2Text:
        '지자체와 지역경제에 최적화된 디지털 지역화폐 플랫폼을 구축합니다. 유통 관리, 사용자 접근성, 정산 편의성을 모두 아우릅니다.',
      service3Title: '공공 인증 인프라',
      service3Text:
        '행정, 교육, 보건 등 다양한 공공 서비스에서 데이터를 안전하게 저장하고 그 진위를 증명할 수 있도록 돕습니다.',
      contactTitle: '연락처',
      formSuccess: '감사합니다! 곧 연락드리겠습니다.',
      nameLabel: '이름',
      emailLabel: '이메일',
      messageLabel: '메시지',
      sendButton: '보내기',
      email: 'contact@kdccy.com',
      footer: '© 2025 한국디지털커런시'
    }
  };

  // Toggle language and save to localStorage
  function toggleLang() {
    lang = lang === 'en' ? 'ko' : 'en';
    localStorage.setItem('lang', lang);
  }

  // Form state
  let name = '';
  let email = '';
  let message = '';
  let formSubmitted = false;

  async function handleSubmit() {
    if (name && email && message) {
      const response = await fetch(CONTACT_URL, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ name, email, message })
      });

      if (response.ok) {
        const result = await response.json();

        if (result.ok) {
          formSubmitted = true;

          console.debug(result);

          name = '';
          email = '';
          message = '';

          setTimeout(() => {
            formSubmitted = false;
          }, 2000);
        }
      }
    }
  }

  let menuOpen = false;

  function toggleMenu() {
    menuOpen = !menuOpen;
  }
</script>

<svelte:head>
  <title>{translations[lang].title}</title>
</svelte:head>

<!-- Header -->
<header class="sticky top-0 z-10 bg-white text-black {scrolled ? 'md:opacity-50' : ''}">
  <nav class="container mx-auto flex items-center justify-between px-6 py-4">
    <h1 class="text-2xl font-bold">{translations[lang].title}</h1>

    <!-- Desktop menu -->
    <ul class="hidden items-center space-x-6 md:flex">
      <li><a href="#home" class="nav-link hover:text-gray-700">{translations[lang].home}</a></li>
      <li><a href="#about" class="nav-link hover:text-gray-700">{translations[lang].about}</a></li>
      <li>
        <a href="#services" class="nav-link hover:text-gray-700">{translations[lang].services}</a>
      </li>
      <li><a href="#team" class="nav-link hover:text-gray-700">{translations[lang].team}</a></li>
      <li>
        <a href="#contact" class="nav-link hover:text-gray-700">{translations[lang].contact}</a>
      </li>
      <li>
        <select
          bind:value={lang}
          on:change={() => localStorage.setItem('lang', lang)}
          class="rounded-lg bg-gray-200 p-2 text-black"
        >
          <option value="ko">한국어</option>
          <option value="en">English</option>
        </select>
      </li>
    </ul>

    <!-- Hamburger button for mobile -->
    <!-- svelte-ignore a11y_consider_explicit_label -->
    <button class="focus:outline-none md:hidden" on:click={toggleMenu}>
      <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M4 6h16M4 12h16M4 18h16"
        />
      </svg>
    </button>
  </nav>

  <!-- Mobile dropdown menu -->
  {#if menuOpen}
    <div
      class="absolute left-0 top-full z-50 w-full border-t border-gray-200 bg-white px-6 py-4 shadow-md md:hidden"
    >
      <ul class="space-y-4">
        <li>
          <a
            href="#home"
            class="nav-link block hover:text-gray-700"
            on:click={() => (menuOpen = false)}>{translations[lang].home}</a
          >
        </li>
        <li>
          <a
            href="#about"
            class="nav-link block hover:text-gray-700"
            on:click={() => (menuOpen = false)}>{translations[lang].about}</a
          >
        </li>
        <li>
          <a
            href="#services"
            class="nav-link block hover:text-gray-700"
            on:click={() => (menuOpen = false)}>{translations[lang].services}</a
          >
        </li>
        <li>
          <a
            href="#team"
            class="nav-link block hover:text-gray-700"
            on:click={() => (menuOpen = false)}>{translations[lang].team}</a
          >
        </li>
        <li>
          <a
            href="#contact"
            class="nav-link block hover:text-gray-700"
            on:click={() => (menuOpen = false)}>{translations[lang].contact}</a
          >
        </li>
        <li>
          <select
            bind:value={lang}
            on:change={() => {
              localStorage.setItem('lang', lang);
              menuOpen = false;
            }}
            class="w-full rounded-lg bg-gray-200 p-2 text-black"
          >
            <option value="ko">한국어</option>
            <option value="en">English</option>
          </select>
        </li>
      </ul>
    </div>
  {/if}
</header>

<!-- Hero Section -->
<section
  id="home"
  class="relative bg-cover bg-center bg-no-repeat py-48"
  style="background-image: url('./hero-bg.png'); filter: grayscale(100%)"
>
  <div class="absolute inset-0 bg-black opacity-70"></div>
  <div class="container relative z-10 mx-auto px-6 text-center">
    <h2 class="mb-6 text-4xl font-bold text-white drop-shadow-lg md:text-6xl">
      {translations[lang].heroTitle}
    </h2>
    <p class="text-md mb-10 text-gray-200 drop-shadow-md md:text-2xl">
      {translations[lang].heroSubtitle}
    </p>
    <a
      href="#contact"
      class="rounded-lg bg-white px-24 py-3 font-semibold text-black transition hover:bg-gray-200"
    >
      {translations[lang].getInTouch}
    </a>
  </div>
</section>

<!-- About Us -->
<section id="about" class="bg-gray-100 py-16">
  <div class="container mx-auto px-6">
    <h2 class="mb-8 text-center text-4xl font-bold">{translations[lang].aboutTitle}</h2>
    <p class="mx-auto max-w-3xl text-center text-xl text-gray-700">
      {translations[lang].aboutText1}
    </p>
    <br />
    <p class="mx-auto max-w-3xl text-center text-xl text-gray-700">
      {translations[lang].aboutText2}
    </p>
    <br />
    <p class="mx-auto max-w-3xl text-center text-xl text-gray-700">
      <strong>{translations[lang].aboutText3}</strong>
    </p>
  </div>
</section>

<!-- Services -->
<section id="services" class="bg-white py-16">
  <div class="container mx-auto px-6">
    <h2 class="mb-8 text-center text-4xl font-bold">
      {translations[lang].servicesTitle}
    </h2>
    <p class="mx-auto mb-12 max-w-3xl text-center text-xl text-gray-700">
      {translations[lang].servicesText1}<br />
      {translations[lang].servicesText2}
    </p>
    <div class="grid grid-cols-1 gap-10 md:grid-cols-3">
      <div class="rounded-2xl bg-white p-6 text-center shadow-lg transition hover:shadow-xl">
        <div class="flex flex-col">
          <div class="flex w-full justify-center rounded-2xl border-2 border-solid p-3">
            <IdCardIcon class="h-48 w-48" />
          </div>
          <h3 class="my-4 text-xl font-semibold">{translations[lang].service1Title}</h3>
          <p class="text-gray-700">{translations[lang].service1Text}</p>
        </div>
      </div>
      <div class="rounded-2xl bg-white p-6 text-center shadow-lg transition hover:shadow-xl">
        <div class="flex flex-col">
          <div class="flex w-full justify-center rounded-2xl border-2 border-solid p-3">
            <BanknoteIcon class="h-48 w-48" />
          </div>
          <h3 class="my-4 text-xl font-semibold">{translations[lang].service2Title}</h3>
          <p class="text-gray-700">{translations[lang].service2Text}</p>
        </div>
      </div>
      <div class="rounded-2xl bg-white p-6 text-center shadow-lg transition hover:shadow-xl">
        <div class="flex flex-col">
          <div class="flex w-full justify-center rounded-2xl border-2 border-solid p-3">
            <LandmarkIcon class="h-48 w-48" />
          </div>
          <h3 class="my-4 text-xl font-semibold">{translations[lang].service3Title}</h3>
          <p class="text-gray-700">{translations[lang].service3Text}</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- Team -->
<section id="team" class="bg-gray-100 py-16">
  <div class="container mx-auto px-6">
    <h2 class="mb-8 text-center text-4xl font-bold">{translations[lang].aboutTeam}</h2>
    <p class="mx-auto max-w-3xl text-center text-xl text-gray-700">
      {translations[lang].aboutTeamText1}
    </p>
    <br />
    <p class="mx-auto max-w-3xl text-center text-xl text-gray-700">
      {translations[lang].aboutTeamText2}
    </p>
    <br />
    <p class="mx-auto max-w-3xl text-center text-xl text-gray-700">
      {translations[lang].aboutTeamText3}
    </p>
  </div>
</section>

<!-- Contact -->
<section id="contact" class="bg-white py-16">
  <div class="container mx-auto px-6">
    <h2 class="mb-8 text-center text-4xl font-bold">{translations[lang].contactTitle}</h2>
    <div class="mx-auto max-w-lg">
      <form on:submit|preventDefault={handleSubmit} class="space-y-4">
        <div>
          <label for="name" class="block text-sm font-medium text-gray-700"
            >{translations[lang].nameLabel}</label
          >
          <input
            bind:value={name}
            id="name"
            type="text"
            class="w-full rounded-lg border border-gray-300 bg-white p-2 text-black"
            required
          />
        </div>
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700"
            >{translations[lang].emailLabel}</label
          >
          <input
            bind:value={email}
            id="email"
            type="email"
            class="w-full rounded-lg border border-gray-300 bg-white p-2 text-black"
            required
          />
        </div>
        <div>
          <label for="message" class="block text-sm font-medium text-gray-700"
            >{translations[lang].messageLabel}</label
          >
          <textarea
            bind:value={message}
            id="message"
            rows="4"
            class="w-full rounded-lg border border-gray-300 bg-white p-2 text-black"
            required
          ></textarea>
        </div>
        <button
          type="submit"
          class="w-full rounded-lg bg-black px-6 py-3 text-white transition hover:bg-gray-800"
        >
          {translations[lang].sendButton}
        </button>
      </form>
    </div>
    <div class="mt-6 text-center text-gray-700">
      <p>{translations[lang].email}</p>
    </div>
    {#if formSubmitted}
      <p class="mb-4 text-center text-gray-700">{translations[lang].formSuccess}</p>
    {/if}
  </div>
</section>

<!-- Footer -->
<footer class="bg-gray-100 py-6">
  <div class="container mx-auto px-6 text-center">
    <p class="text-black">{translations[lang].footer}</p>
    <div class="mt-2">
      <a href="#home" class="mx-2 text-gray-700 hover:text-black">{translations[lang].home}</a>
      <a href="#about" class="mx-2 text-gray-700 hover:text-black">{translations[lang].about}</a>
      <a href="#services" class="mx-2 text-gray-700 hover:text-black"
        >{translations[lang].services}</a
      >
      <a href="#team" class="mx-2 text-gray-700 hover:text-black">{translations[lang].team}</a>
      <a href="#contact" class="mx-2 text-gray-700 hover:text-black">{translations[lang].contact}</a
      >
    </div>
  </div>
</footer>
