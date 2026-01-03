# App Documentos Jurídicos (Expo)

Aplicativo mobile em React Native/Expo para gestão de casos e documentos jurídicos.

## Status rápido
- Projeto focado em mobile (Expo). Não há fluxo de build e assinatura (signing) configurado ainda.
- É necessário configurar variáveis de ambiente para Firebase (contas/documentos) e Supabase. Veja `.env.example`.
- Recomendado revisar regras de segurança do Firestore/Storage e Supabase antes de produção.

## Como rodar localmente
1. Instale dependências: `npm install`
2. Copie o arquivo `.env.example` para `.env` e preencha com suas chaves.
3. Inicie em desenvolvimento:
   - Mobile: `npm start` e abra com Expo Go
   - Web (para validar): `npm run web` (atalho para `expo start --web`)

## O que falta para produção
- Definir as chaves reais de Firebase/Supabase no `.env` e configurar regras de segurança.
- Não versionar chaves reais; use variáveis de ambiente diferentes por ambiente (dev/homolog/prod).
- Configurar fluxo de build/assinatura (EAS Build) para gerar APK/AAB/IPA.
- (Opcional web) Validar quais telas/recursos funcionam no navegador e ajustar o que depender de APIs apenas nativas.

## Deploy em Vercel ou Netlify
O app é pensado para mobile. Para publicar em Vercel/Netlify é necessário usar a versão web exportada do Expo:

1. Gere o build web estático:
   ```bash
   npx expo export --platform web --output-dir dist
   ```
2. Configure o provedor e garanta que as variáveis de ambiente estejam definidas antes do build:
   - **Vercel**
     - Install command: `npm install`
     - Build command: usar o comando do passo 1 (`npx expo export --platform web --output-dir dist`)
     - Output directory: `dist`
   - **Netlify**
     - Build command: usar o comando do passo 1 (`npx expo export --platform web --output-dir dist`)
     - Publish directory: `dist`
3. Cadastre no painel as mesmas variáveis de ambiente do `.env` antes de rodar o build.

Para distribuir em dispositivos móveis, use o `expo start` para testes e configure builds via EAS (mais recomendado para produção).
