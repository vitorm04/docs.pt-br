### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad não deve ser usado no arquivo de funcionalidades personalizadas, pois agora é uma funcionalidade do navegador

|   |   |
|---|---|
|Detalhes|A partir do .NET 4.5, o iPad é um identificador no arquivo de funcionalidades do navegador ASP.NET padrão, então, não pode ser usado em um arquivo de funcionalidades personalizadas.|
|Sugestão|Se funcionalidades específicas do iPad forem exigidas, será necessário modificar o comportamento dele configurando funcionalidades na refID do gateway predefinido &quot;IPad&quot; em vez de gerar uma nova ID &quot;IPad&quot; pela correspondência do agente do usuário.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|

