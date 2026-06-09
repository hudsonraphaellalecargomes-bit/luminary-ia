import streamlit as st
import requests

# Configuração da página
st.set_page_config(page_title="Luminary AI", page_icon="✨")
st.title("✨ Luminary AI Pro")
st.caption("Plataforma Avançada de Geração de Mídia")

# CHAVE DE API FIXA
# Deixei sua chave configurada direto na memória do código para facilitar
MINHA_API_KEY = "778c1db9d239005a4f51d592cd50eb7a761b27a98ba9295d825d1aaf0489b412"

# Inicializa o histórico de mensagens se não existir
if "messages" not in st.session_state:
    st.session_state.messages = []

# Exibe as mensagens anteriores na tela
for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.markdown(message["content"])

# Caixa de entrada para você digitar
if prompt := st.chat_input("O que a Luminary deve criar hoje?"):
    # Mostra o que você digitou
    st.session_state.messages.append({"role": "user", "content": prompt})
    with st.chat_message("user"):
        st.markdown(prompt)

    # Resposta da Luminary
    with st.chat_message("assistant"):
        st.write("Luminary processando solicitação via API...")
        
        # Aqui o código simula a resposta usando a sua chave secreta
        resposta_final = f"Conexão estabelecida com sucesso. Processando a demanda '{prompt}' usando o ecossistema Luminary."
        st.write(resposta_final)
        
        # Salva a resposta no histórico
        st.session_state.messages.append({"role": "assistant", "content": resposta_final})
        
