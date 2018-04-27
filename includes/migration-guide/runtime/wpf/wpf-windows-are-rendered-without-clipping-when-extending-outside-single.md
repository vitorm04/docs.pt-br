### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Janelas do WPF são renderizadas sem distorção ao se estender para fora de um único monitor

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6 em execução no Windows 8 e superior, a janela inteira é renderizada sem distorção quando ela se estende para fora da exibição única em um cenário de vários monitores. Isso é diferente de versões anteriores do .NET Framework, que distorceriam janelas do WPF que se estendiam para fora de uma única exibição.|
|Sugestão|Esse comportamento (com distorção ou não) pode ser definido explicitamente usando o elemento <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> em <code>&lt;appSettings&gt;</code> no arquivo de configuração do aplicativo ou definindo a propriedade <code>EnableMultiMonitorDisplayClipping</code> durante a inicialização do aplicativo.|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Tempo de execução|

