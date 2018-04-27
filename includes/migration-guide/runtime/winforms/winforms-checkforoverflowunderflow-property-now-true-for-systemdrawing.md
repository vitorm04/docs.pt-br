### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>A propriedade CheckForOverflowUnderflow do WinForm agora é true para System.Drawing

|   |   |
|---|---|
|Detalhes|A propriedade CheckForOverflowUnderflow do o assembly System.Drawing.dll está definida como true.|
|Sugestão|Anteriormente, quando os estouros ocorriam, o resultado teria sido truncado silenciosamente. Agora, uma exceção <xref:System.OverflowException?displayProperty=name> é gerada.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|

