import streamlit as st

# Configuración profesional de la página
st.set_page_config(page_title="Ingeniería de Sartas - Tesis", layout="wide")

# Título principal basado en tu tesis
st.title("🏗️ Calculadora de Ingeniería de Perforación")
st.markdown("### Basado en la Sección 2.3 de la Tesis")

# --- PANEL LATERAL (ENTRADAS) ---
st.sidebar.header("📋 Parámetros de Entrada")
barrena = st.sidebar.slider("Diámetro de Barrena (in)", 4.0, 26.0, 8.5)
densidad_lodo = st.sidebar.number_input("Densidad del lodo (g/cm³)", value=1.20)

# --- CUERPO PRINCIPAL (SECCIONES 2.3.1 A 2.3.7) ---
tab1, tab2, tab3 = st.tabs(["2.3.1 - 2.3.2 Kelly y Subs", "2.3.3 - 2.3.4 Tuberías", "2.3.5 - 2.3.7 Lastrabarrenas"])

with tab1:
    st.header("Componentes Superiores")
    col1, col2 = st.columns(2)
    with col1:
        st.subheader("2.3.1 Flecha (Kelly)")
        kelly = st.selectbox("Tipo de Flecha", ["Cuadrada", "Hexagonal"])
        st.info(f"La flecha {kelly} se encarga de transmitir el torque.")
    with col2:
        st.subheader("2.3.2 Sustitutos (Subs)")
        st.write("Válvulas y protectores seleccionados:")
        st.checkbox("Kelly Cock (Válvula de seguridad)")
        st.checkbox("Saver Sub (Sustituto de desgaste)")

with tab2:
    st.header("Tubería de Perforación (TP) y Pesada (HWDP)")
    col3, col4 = st.columns(2)
    with col3:
        st.subheader("2.3.3 Grados de TP")
        grado = st.selectbox("Seleccione el Grado", ["E-75", "X-95", "G-105", "S-135"])
        st.success(f"Resistencia seleccionada: {grado}")
    with col4:
        st.subheader("2.3.4 HWDP")
        st.write("Tubería de pared gruesa usada como zona de transición para evitar fatiga en la TP.")

with tab3:
    st.header("Diseño de Lastrabarrenas (Drill Collars)")
    st.subheader("2.3.6 Tipos de DC")
    tipo_dc = st.radio("Configuración:", ["Liso (Slick)", "Espiral (Antipegadura)", "No Magnético (Monel)"])
    
    st.markdown("---")
    st.subheader("2.3.7 Cálculos de Ingeniería")
    
    # Cálculos automáticos
    ff = 1 - (densidad_lodo / 7.85)  # Factor de flotación
    dc_ideal = barrena * 0.82        # Estimación técnica de diámetro de DC
    
    c1, c2 = st.columns(2)
    c1.metric("Factor de Flotación (FF)", f"{ff:.3f}")
    c2.metric("DC Recomendado", f"{dc_ideal:.2f} pulgadas")
    
    if tipo_dc == "Espiral (Antipegadura)":
        st.warning("Recomendado para evitar pegaduras por presión diferencial.")

st.markdown("---")
st.caption("Cálculos realizados según parámetros técnicos de la sarta de perforación.")
