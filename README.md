# Correção do pareamento (QR) da Evolution API 2.3.7

Problema: desde ~28/07/2026 o WhatsApp mudou uma etapa do pareamento e o Baileys do 2.3.7 não conclui o QR (celular mostra "não foi possível conectar"). Sessões já conectadas seguem; o que quebra é parear de novo.

Correção usada: branch `fix/baileys-pairing-main` do fork ErgoCodes/evolution-api (PR #2759 do projeto oficial, ainda aberto), commit `d0198733da3cb133bd0c64d24fc4d1e7720696b1`, base 2.3.7 + Baileys rc14 + patch de 4 arquivos (lido: sem chamadas externas, eval ou leitura de variáveis de ambiente).

O Gerenciador Docker da Hostinger NÃO monta imagem (só baixa pronta): a tentativa com `build:` falhou em 27/10 e foi revertida para `evoapicloud/evolution-api:latest`.

Caminho: montar a imagem no GitHub Actions e publicar em `ghcr.io/<usuario>/evolution-api-pairing:2.3.7-rc14`, deixar o pacote público e trocar só a linha `image:` do serviço `api`. Workflow: `build-evolution-pairing.yml`.
