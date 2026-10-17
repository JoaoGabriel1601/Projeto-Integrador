# Repositório da organização

Destino: https://github.com/expotech2026-2/EXPOTECH2026-2 (privado).

A importação foi concluída em 16/10/2026. Ela criou uma cópia do histórico;
alterações posteriores no repositório pessoal não são sincronizadas automaticamente.
O remoto local `organization` identifica a cópia da equipe. Para enviar a main:

```sh
git push organization main
```

O repositório pessoal continua no remoto `origin`. As cópias não foram excluídas
nem tiveram seu histórico reescrito. `vercel.json` mantém o autodeploy Git da Vercel
desativado.

## Acesso da equipe

Em Settings → Collaborators and teams, o proprietário pode adicionar pessoas ou
equipes e atribuir o papel Admin especificamente neste repositório. Esse papel
permite administrar configurações e acessos; não exige tornar todos proprietários
da organização. Convites precisam ser aceitos pelos destinatários.

## Verificações automáticas

- `Validação Movement`: lint, testes, sincronização de constantes, build web e
  testes da API com PostgreSQL no runner. Docker local não é necessário.
- `CodeQL Advanced`: a falha original de C/C++ era `No source files found`, pois
  o extrator não reconhecia `.ino`. O workflow prepara uma cópia temporária
  `.ino.cpp` de cada sketch antes da extração; o firmware original é preservado.
  A análise sem build tem precisão limitada pelas bibliotecas Arduino/ESP32
  ausentes no runner e não substitui compilação e testes no dispositivo.
- CodeQL funciona gratuitamente em repositórios públicos. Para um repositório
  privado de organização é necessário habilitar GitHub Code Security em plano
  compatível. Após confirmar a licença, configure a variável de Actions
  `ENABLE_PRIVATE_CODEQL=true`. Sem isso, o workflow informa a indisponibilidade
  no resumo e marca as análises como não executadas, sem alegar aprovação.

Referências oficiais:
- https://docs.github.com/en/code-security/reference/code-scanning/troubleshoot-analysis-errors/private-repository-enablement
- https://docs.github.com/en/code-security/reference/code-scanning/codeql/build-options-for-compiled-languages

## Alerta de credencial histórica

O GitHub notificou uma possível Google API Key em `FIREBASE_SETUP.md`, commit
`4b5adc03`, na cópia pessoal `JoaoGabriel1601/EXPOTECH2026-2`. O arquivo já não
existe na versão atual, mas permanece no histórico importado. Um commit novo não
revoga uma chave antiga. O responsável pelo projeto Google deve conferir o alerta
e revogar/substituir a chave no provedor se válida, verificando consumidores antes.
Não publicar a chave, fechar o alerta como resolvido sem validação, nem reescrever
histórico compartilhado como substituto da revogação.
