### <a name="serialport-background-thread-exceptions"></a>Exceções de thread de tela de fundo de SerialPort

|   |   |
|---|---|
|Detalhes|Threads criados com fluxos <xref:System.IO.Ports.SerialPort> em segundo plano não terminam mais o processo quando exceções de sistema operacional são lançadas. Em aplicativos destinados ao .NET Framework 4.7 e a versões anteriores, um processo é terminado quando uma exceção do sistema operacional é gerada em um thread de segundo plano criado com um fluxo <xref:System.IO.Ports.SerialPort>. Em aplicativos destinados ao .NET Framework 4.7.1 ou a uma versão posterior, threads em segundo plano esperam eventos do sistema operacional relacionadas à porta serial ativa e podem falhar em alguns casos, como no caso de remoção repentina da porta serial.|
|Sugestão|Para aplicativos destinados ao .NET Framework 4.7.1, será possível recusar a manipulação de exceções se ela não for desejável adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo <code>app.config</code>:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Para aplicativos destinados a versões anteriores do .NET Framework mas executados no .NET Framework 4.7.1 ou posterior, é possível aceitar a manipulação de exceções adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo <code>app.config</code>:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

