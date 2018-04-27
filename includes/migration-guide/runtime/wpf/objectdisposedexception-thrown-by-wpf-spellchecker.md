### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException gerada pelo verificador ortográfico do WPF

|   |   |
|---|---|
|Detalhes|Ocasionalmente, os aplicativos WPF falham durante o desligamento com uma <xref:System.ObjectDisposedException?displayProperty=name> gerada pelo verificador ortográfico. Isso foi corrigido no WPF do .NET 4.7 por meio do tratamento normal da exceção e, dessa forma, garantindo que os aplicativos não sejam mais afetados de forma negativa. Observe que exceções de primeira chance ocasionais continuariam a ser observadas em aplicativos em execução em um depurador.|
|Sugestão|Atualizar para .NET 4.7|
|Escopo|Microsoft Edge|
|Versão|4.6.1|
|Tipo|Tempo de execução|

