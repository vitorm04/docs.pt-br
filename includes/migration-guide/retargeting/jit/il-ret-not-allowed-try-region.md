### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret não é permitido em uma região try

|   |   |
|---|---|
|Detalhes|Ao contrário do compilador Just-In-Time JIT64, o RyuJIT (usado no .NET 4.6) não permite uma instrução IL ret em uma região try. Retornar de uma região try não é permitido pela especificação ECMA-335, e nenhum compilador gerenciado conhecido gera tal IL. No entanto, o compilador JIT64 executará essa IL se ela for gerada usando emissão de reflexo.|
|Sugestão|Se um aplicativo estiver gerando ILs que incluam um opcode ret em uma região try, o aplicativo poderá ser destinado ao .NET 4.5 para usar o JIT antigo e evitará essa interrupção. Como alternativa, a IL gerada pode ser atualizado para retornar após a região try.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Redirecionando|

