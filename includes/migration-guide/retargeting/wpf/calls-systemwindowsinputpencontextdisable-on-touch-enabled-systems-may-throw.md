### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException

|   |   |
|---|---|
|Detalhes|Em algumas circunstâncias, chamadas para o método interno <strong>System.Windows.Intput.PenContext.Disable</strong> em sistemas habilitados para toque podem gerar uma <code>T:System.ArgumentException</code> sem tratamento devido à reentrância.|
|Sugestão|Esse problema foi resolvido no .NET Framework 4.7. Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.|
|Escopo|Microsoft Edge|
|Versão|4.6.1|
|Tipo|Redirecionando|

