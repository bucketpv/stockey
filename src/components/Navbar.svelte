<script>
  import { Package, Download } from 'lucide-svelte';
  export let onDownload;
</script>

<header class="navbar-container">
  <div class="content-wrapper navbar-flex">
    <div class="brand-logo">
        <img src="/stockey/favicon.svg" alt="Stockey" style="width: 32px; height: 32px;" />
      <span class="brand-name">Stockey</span>
    </div>
    <nav class="nav-links">
      <a href="#features">Características</a>
      <a href="#licencias">Licencias</a>
      <a href="#arquitectura">¿Cómo funciona?</a>
      <button class="btn-primary btn-sm" on:click={onDownload}>
        <Download size={14} /> Descargar
      </button>
    </nav>
  </div>
</header>

<style>
  .navbar-container {
    background: rgba(255, 255, 255, 0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid #e2e8f0;
    position: sticky;
    top: 0;
    z-index: 100;
    width: 100%;
  }
  .navbar-flex {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 64px;
  }
  .brand-logo {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .icon-accent-box {
    background: #2563eb;
    color: #ffffff;
    width: 32px;
    height: 32px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .brand-name {
    font-size: 1.2rem;
    font-weight: 900;
    letter-spacing: -0.5px;
    color: #0f172a;
  }
  .dot-accent { color: #2563eb; }
  .nav-links {
    display: flex;
    align-items: center;
    gap: 24px;
  }
  .nav-links a {
    text-decoration: none;
    color: #475569;
    font-weight: 600;
    font-size: 0.85rem;
    transition: color 0.15s;
  }
  .nav-links a:hover { color: #2563eb; }
</style>