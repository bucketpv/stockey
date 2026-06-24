<script>
  import { Monitor, Cpu, HardDrive, CheckCircle2, ShieldAlert } from 'lucide-svelte';

  const specs = [
    {
      icon: Monitor,
      label: "Sistema Operativo",
      value: "Windows 10 / Windows 11",
      detail: "Compatible con arquitecturas estándar de estaciones de trabajo y laptops."
    },
    {
      icon: Cpu,
      label: "Conectividad",
      value: "Ejecución Local y Autónoma",
      detail: "Funciona sin internet. Sin servidores que configurar. Sin cuotas mensuales."
    },
    {
      icon: HardDrive,
      label: "Almacenamiento",
      value: "Instalación Ligera y Rápida",
      detail: "Aplicación de alto rendimiento que se instala limpiamente en segundos."
    }
  ];
</script>

<section id="requisitos" class="requirements-section">
  <div class="content-wrapper">
    <div class="requirements-box">
      <div class="req-header">
        <div class="req-title-group">
          <span class="badge badge-tech">Compatibilidad</span>
          <h2>Especificaciones de Ejecución</h2>
        </div>
        <p class="req-subtitle">
          Stockey ha sido desarrollado para ofrecer el máximo rendimiento sin saturar los recursos de hardware de tu negocio. Funciona en cualquier equipo de escritorio o portatil destinado a la operación diaria.
        </p>
      </div>

      <div class="req-grid">
        {#each specs as spec}
          <div class="req-card">
            <div class="req-icon-frame">
              <svelte:component this={spec.icon} size={20} />
            </div>
            <div class="req-info">
              <span class="req-label">{spec.label}</span>
              <strong class="req-value">{spec.value}</strong>
              <p class="req-detail">{spec.detail}</p>
            </div>
            <div class="req-status">
              <CheckCircle2 size={16} class="text-success" />
            </div>
          </div>
        {/each} 
      </div>

      <!-- Aviso simplificado y más directo -->
      <div class="req-footer-note">
        <ShieldAlert size={16} class="text-warning-icon" />
        <p>
          <strong>Sin dependencia de la nube:</strong> Stockey se auto-configura durante la instalación. No requiere infraestructura externa ni mantenimiento técnico.
        </p>
      </div>
    </div>
  </div>
</section>

<style>
  .requirements-section {
    padding: 60px 0;
    background: #f8fafc;
    width: 100%;
  }

  .requirements-box {
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 16px;
    padding: 40px;
    box-shadow: 0 4px 12px rgba(15, 23, 42, 0.01);
  }

  .req-header {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 40px;
    align-items: center;
    border-bottom: 1px solid #f1f5f9;
    padding-bottom: 32px;
    margin-bottom: 32px;
  }

  .req-title-group h2 {
    font-size: 1.8rem;
    font-weight: 800;
    color: #0f172a;
    letter-spacing: -0.5px;
    margin-top: 8px;
  }

  .badge-tech {
    background: #f1f5f9;
    color: #475569;
    border: 1px solid #e2e8f0;
    display: inline-block;
    padding: 4px 12px;
    border-radius: 9999px;
    font-size: 0.72rem;
    font-weight: 700;
  }

  .req-subtitle {
    font-size: 0.95rem;
    color: #475569;
    line-height: 1.6;
  }

  .req-grid {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .req-card {
    display: flex;
    align-items: center;
    gap: 20px;
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 10px;
    padding: 20px 24px;
    transition: border-color 0.15s;
  }

  .req-card:hover {
    border-color: #cbd5e1;
  }

  .req-icon-frame {
    width: 40px;
    height: 40px;
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 8px;
    color: #2563eb;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  .req-info {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .req-label {
    font-size: 0.75rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    color: #64748b;
    margin-bottom: 2px;
  }

  .req-value {
    font-size: 1rem;
    font-weight: 700;
    color: #0f172a;
  }

  .req-detail {
    font-size: 0.85rem;
    color: #64748b;
    margin-top: 2px;
  }

  .req-status {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  .req-footer-note {
    margin-top: 32px;
    background: #fffbeb;
    border: 1px solid #fef3c7;
    padding: 16px 20px;
    border-radius: 8px;
    display: flex;
    gap: 12px;
    align-items: center;
    font-size: 0.85rem;
    color: #b45309;
  }

  .text-warning-icon {
    color: #d97706;
    flex-shrink: 0;
  }

  .text-success { color: #16a34a; }

  @media (max-width: 768px) {
    .req-header {
      grid-template-columns: 1fr;
      gap: 16px;
    }
    .req-card {
      padding: 16px;
    }
  }
</style>