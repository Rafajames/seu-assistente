# Seu Assistente – APK para Android

Projeto Capacitor que embute o app web (`www/`) num app Android, com notificações agendadas pelo sistema (tocam com o app fechado) e ditado de voz nativo.

## Gerar o APK (sem instalar nada no seu computador)
1. Crie um repositório novo no GitHub (pode ser privado) e envie **todo o conteúdo desta pasta**, incluindo a pasta oculta `.github`.
   - Pelo site: **Add file → Upload files**. Arraste também a pasta `.github/workflows` (se o navegador não aceitar, use **Add file → Create new file** e cole o conteúdo de `build-apk.yml` com o nome `.github/workflows/build-apk.yml`).
2. Abra a aba **Actions**. O fluxo "Compilar APK" roda sozinho a cada envio (cerca de 5 a 8 minutos). Também dá para rodar em **Run workflow**.
3. Quando ficar verde, abra a execução e baixe **seu-assistente-apk** em *Artifacts*. Dentro do zip está `app-debug.apk`.
4. Passe o APK para o celular e abra. O Android pede para permitir "instalar apps de fontes desconhecidas". É um APK de teste, assinado com a chave de depuração.

## Ao abrir pela primeira vez
- Em **Ajustes → Notificações do sistema → Ativar**, permita as notificações (Android 13 ou mais novo).
- Para lembretes na hora exata, em Android 12 ou mais novo vá em Configurações → Apps → Seu Assistente → "Alarmes e lembretes" e permita.
- Em aparelhos Xiaomi, Samsung, Motorola e similares, tire o app da economia de bateria, senão o sistema pode atrasar os avisos.

## O que funciona neste APK
- Tarefas, diário, repetições, prioridade automática, gamificação, temas e acessibilidade.
- Lembretes agendados com o sistema, inclusive com o app fechado. A cada alteração o app reagenda os próximos 60 avisos, mais lembretes insistentes para tarefas atrasadas.
- Ditado de voz nativo (microfone dos ajustes de voz do Android).
- Backup: compartilhar o arquivo ou copiar o texto; restaurar do arquivo ou do texto copiado.

## O que ainda não está neste APK
- **Login na nuvem** (Google, Dropbox, OneDrive): o Google bloqueia login dentro de WebView. Falta usar um plugin de login nativo. A versão web já sincroniza.
- **Palavra de ativação "Assistente"** com a tela apagada.
- **Modo foco que trava o celular** (bloqueio real). Hoje ele é só uma tela cheia dentro do app.
- **Aviso por localização com o app fechado.**
- **Assinatura de loja:** para publicar na Play Store é preciso gerar um bundle assinado (`./gradlew bundleRelease`) com sua chave.

## Editar o app
O código do app está em `www/index.html`. Depois de mudar, envie ao GitHub e o APK é recompilado.
Para compilar no seu computador: Node 22, JDK 21 e Android Studio; rode `npm install`, `npx cap sync android` e abra a pasta `android` no Android Studio.
