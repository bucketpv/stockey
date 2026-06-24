<script>
  import { Check, ShieldCheck, Star } from 'lucide-svelte';

  let showModal = false;
  let licenseRequested = false;
  let emailInput = "";

  const tiers = [
    {
      name: "Licencia de Evaluación",
      price: "Gratis",
      period: "por 14 días",
      desc: "Acceda a la suite operativa completa para evaluar las herramientas en su entorno comercial.",
      features: ["Control completo de catálogo", "Punto de venta básico", "Métricas básicas de utilidad", "Soporte documentado vía GitHub"],
      action: "Iniciar Evaluación",
      highlight: false
    },
    {
      name: "Licencia Comercial Anual",
      price: "$49.000",
      period: "al año",
      desc: "Orientado a empresas activas que requieren soporte operativo continuo y actualizaciones de estabilidad.",
      features: ["Todo lo de la Licencia de Evaluación", "Módulo avanzado de proveedores", "Alertas automáticas de existencias críticas", "Actualizaciones periódicas de seguridad"],
      action: "Adquirir Licencia Anual",
      highlight: true
    },
    {
      name: "Licencia Permanente",
      price: "$119.000",
      period: "pago único",
      desc: "Para organizaciones que buscan la máxima autonomía del software, eliminando los costos recurrentes.",
      features: ["Todo lo de la Licencia Anual", "Inversión única vitalicia", "Cero dependencias de renovación anual", "Soporte prioritario uno a uno"],
      action: "Adquirir de por Vida",
      highlight: false
    }
  ];

  function openRequestModal() {
    showModal = true;
    licenseRequested = false;
  }

  function handleRequest(e) {
    e.preventDefault();
    if (emailInput.trim() !== "") {
      licenseRequested = true;
    }
  }

  // Acción para botones de compra (WhatsApp)
  function openWhatsApp(planName) {
    const message = encodeURIComponent(
      `¡Hola! Estoy interesado en el plan "${planName}" de Stockey. ¿Podrías darme más información?`
    );
    window.open(`https://wa.me/569XXXXXXXX?text=${message}`, '_blank');
  }
</script>

<section id="licencias" class="pricing-section">
  <div class="content-wrapper">
    <div class="text-center" style="margin-bottom: 50px;">
      <span class="badge badge-accent">Inversión Transparente</span>
      <h2 class="section-title" style="margin-top: 12px; text-align: center;">Planes estructurados para la sostenibilidad</h2>
      <p class="section-subtitle" style="margin: 12px auto 0 auto; text-align: center;">
        Ofrecemos un esquema comercial claro y directo, eliminando los cobros mensuales imprevistos o las suscripciones obligatorias.
      </p>
    </div>

    <div class="pricing-grid">
      {#each tiers as tier}
        <div class="pricing-card" class:highlighted={tier.highlight}>
          {#if tier.highlight}
            <span class="pop-badge"><Star size={12} /> Sugerido</span>
          {/if}
          <h3>{tier.name}</h3>
          <div class="price-box">
            <span class="amount">{tier.price}</span>
            <span class="period">/ {tier.period}</span>
          </div>
          <!-- Equivalencia mensual para la licencia anual -->
          {#if tier.period === 'al año'}
            <p class="monthly-equivalent">Equivale a $4.083/mes</p>
          {/if}
          <p class="desc">{tier.desc}</p>
          
          <hr class="divider" />

          <ul class="feat-list">
            {#each tier.features as feat}
              <li><Check size={16} class="text-success" /> {feat}</li>
            {/each}
          </ul>

          {#if tier.price === "Gratis"}
            <button class="btn-tier-action btn-secondary-tier" on:click={openRequestModal}>
              {tier.action}
            </button>
          {:else}
            <button class="btn-tier-action" class:btn-primary-tier={tier.highlight} class:btn-secondary-tier={!tier.highlight} on:click={() => openWhatsApp(tier.name)}>
              {tier.action}
            </button>
          {/if}
        </div>
      {/each}
    </div>
  </div>
</section>

{#if showModal}
  <div class="modal-backdrop">
    <div class="modal-box">
      <button class="close-btn" on:click={() => showModal = false}>&times;</button>
      
      {#if !licenseRequested}
        <div class="text-center">
          <ShieldCheck size={40} style="color: #2563eb; margin-bottom: 12px; margin-inline: auto;" />
          <h3 style="text-align: center;">Prueba gratuita de 14 días</h3>
          <p style="font-size: 0.9rem; color: #475569; margin-top: 8px; text-align: center;">
            Déjanos tu correo y te enviaremos el código de activación para empezar a usar Stockey sin límites.
          </p>
        </div>
        <form on:submit={handleRequest} style="margin-top: 20px;">
          <input 
            type="email" 
            placeholder="Ejemplo: contacto@empresa.com" 
            bind:value={emailInput} 
            required 
            class="modal-input" 
          />
          <button type="submit" class="btn-primary" style="width: 100%; padding: 12px; border-radius: 6px; margin-top: 12px; font-weight: 600; justify-content: center;">
            Solicitar código de prueba
          </button>
        </form>
      {:else}
        <div class="text-center" style="padding: 20px 0;">
          <span style="font-size: 2.5rem; display: block; text-align: center;">📬</span>
          <h3 style="margin-top: 12px; text-align: center;">¡Revisa tu correo!</h3>
          <p style="font-size: 0.9rem; color: #475569; margin-top: 8px; text-align: center;">
            En unos minutos recibirás las instrucciones para activar tu prueba gratuita de 14 días.
          </p>
          <button class="btn-ghost" style="margin-top: 20px; width: 100%; padding: 10px; border-radius: 6px; justify-content: center;" on:click={() => showModal = false}>
            Entendido
          </button>
        </div>
      {/if}
    </div>
  </div>
{/if}

<style>
  .pricing-section { padding: 90px 0; background: #f8fafc; width: 100%; }
  .pricing-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 32px; margin-top: 40px; align-items: stretch; }
  
  .pricing-card { background: #ffffff; border: 1px solid #e2e8f0; border-radius: 14px; padding: 32px; display: flex; flex-direction: column; position: relative; transition: transform 0.2s; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.02); }
  .pricing-card.highlighted { border-color: #2563eb; box-shadow: 0 10px 25px -5px rgba(37, 99, 235, 0.1); transform: scale(1.02); }
  
  .pop-badge { position: absolute; top: -12px; left: 32px; background: #2563eb; color: white; font-size: 0.7rem; font-weight: 700; padding: 4px 12px; border-radius: 9999px; display: inline-flex; align-items: center; gap: 4px; }
  
  .pricing-card h3 { font-size: 1.2rem; font-weight: 700; color: #0f172a; text-align: left; }
  .price-box { margin: 16px 0 4px 0; display: flex; align-items: baseline; gap: 4px; justify-content: flex-start; }
  .amount { font-size: 2.25rem; font-weight: 800; color: #0f172a; }
  .period { color: #64748b; font-size: 0.9rem; }
  .monthly-equivalent { font-size: 0.8rem; color: #16a34a; font-weight: 600; margin-bottom: 8px; }
  .desc { font-size: 0.85rem; color: #475569; min-height: 48px; line-height: 1.5; text-align: left; }
  
  .divider { border: 0; border-top: 1px solid #f1f5f9; margin: 20px 0; }
  
  .feat-list { list-style: none; display: flex; flex-direction: column; gap: 12px; margin-bottom: 32px; flex-grow: 1; padding: 0; }
  .feat-list li { font-size: 0.85rem; color: #334155; display: flex; align-items: flex-start; gap: 10px; text-align: left; }
  .text-success { color: #16a34a; flex-shrink: 0; }
  
  .btn-tier-action { width: 100%; padding: 12px; border-radius: 8px; font-weight: 600; font-size: 0.9rem; text-align: center; cursor: pointer; transition: background 0.15s; font-family: inherit; display: flex; justify-content: center; align-items: center; border: none; }
  .btn-primary-tier { background: #2563eb; color: white; }
  .btn-primary-tier:hover { background: #1d4ed8; }
  .btn-secondary-tier { background: transparent; color: #2563eb; border: 1px solid #bfdbfe; }
  .btn-secondary-tier:hover { background: #eff6ff; }

  .modal-backdrop { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(15, 23, 42, 0.6); backdrop-filter: blur(4px); display: flex; align-items: center; justify-content: center; z-index: 200; padding: 20px; }
  .modal-box { background: white; padding: 32px; border-radius: 12px; width: 100%; max-width: 440px; position: relative; box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1); box-sizing: border-box; }
  .close-btn { position: absolute; top: 16px; right: 16px; background: transparent; border: none; font-size: 1.5rem; color: #94a3b8; cursor: pointer; }
  .modal-input { width: 100%; padding: 12px; border: 1px solid #cbd5e1; border-radius: 6px; font-size: 0.9rem; outline: none; font-family: inherit; box-sizing: border-box; }
  .modal-input:focus { border-color: #2563eb; box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1); }
  .badge-accent { background: #eff6ff; color: #2563eb; padding: 4px 12px; border-radius: 9999px; font-size: 0.72rem; font-weight: 700; display: inline-block; }
</style>