### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Geração de código incorreto ao passar e comparar valores UInt16

|   |   |
|---|---|
|Detalhes|Em virtude das alterações realizadas no .NET Framework 4.7, em alguns casos, o código gerado pelo compilador JIT em aplicativos em execução no .NET Framework 4.7 é incorretamente comparado com dois valores <code>T:System.UInt16</code>. Para saber mais, consulte, [Issue #11508: Silent bad codegen when passing and comparing ushort args](https://github.com/dotnet/coreclr/issues/11508) (Problema nº11508: Geração de código silenciosa incorreta ao passar e comparar args ushor), no GitHub.com.|
|Sugestão|Se houver problemas na comparação dos valores sem sinal de 16 bits no .NET Framework 4.7, atualize para o .NET Framework 4.7.1.|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Tempo de execução|

