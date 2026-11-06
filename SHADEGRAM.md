# Shadegram

Cliente open source baseado no [Telegram iOS](https://github.com/TelegramMessenger/Telegram-iOS) (GPL v2),
com a tela de Configurações e a troca de contas mais privadas: uma conta pode ficar oculta e só aparece
depois de um código digitado na busca de Configurações.

Uso pessoal, sem publicação na App Store. O IPA é gerado pelo GitHub Actions e instalado com Sideloadly.

## Comandos (busca de Configurações)

| Digite | Efeito |
|---|---|
| `#shade:SEUCODIGO#` | Oculta a conta **atual** e define o código (mínimo 4 caracteres). O app troca para outra conta. |
| `SEUCODIGO` | Revela as contas ocultas e troca para a conta oculta. Digitar de novo esconde. |
| `#shadeoff:SEUCODIGO#` | Desfaz tudo (só com o modo revelado). |

Ao ir para segundo plano, o app volta a esconder e sai da conta oculta.

Enquanto oculta, a conta não aparece em: lista de contas das Configurações, seletor da aba
(toque longo), atalhos do ícone, avatar/badge da aba e busca de Configurações.

## Mudanças em relação ao Telegram

- `submodules/AccountUtils/Sources/ShadeAccounts.swift` — lógica das contas ocultas.
- `submodules/AccountUtils/Sources/AccountUtils.swift` — filtro na lista central de contas.
- `submodules/SettingsUI/Sources/Search/SettingsSearchItem.swift` — comandos na busca.
- `submodules/TelegramUI/Sources/AppDelegate.swift` — funciona sem App Group (Apple ID grátis).
- `build-system/Make/Make.py` — `--shadeDisableExtensions`.
- `.github/workflows/build.yml` — build do IPA.

## Build

Secrets `TELEGRAM_API_ID` e `TELEGRAM_API_HASH` (de my.telegram.org), depois
Actions → **Build Shadegram** → Run workflow. O IPA sai como artefato da execução.
