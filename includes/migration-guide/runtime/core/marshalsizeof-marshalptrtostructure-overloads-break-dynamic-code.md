### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>As sobrecargas Marshal.SizeOf e Marshal.PtrToStructure interrompem o código dinâmico

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5.1, a associação dinâmica aos métodos <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> ou <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (por meio do Windows PowerShell, IronPython ou da palavra-chave dinâmica do C#, por exemplo) pode resultar em <code>MethodInvocationExceptions</code>, pois novas sobrecargas desses métodos que foram adicionadas podem ser ambíguas para os mecanismos de script.|
|Sugestão|Atualize os scripts para indicar claramente qual sobrecarga deve ser usada. Normalmente, isso pode ser feito convertendo explicitamente os parâmetros de tipo dos métodos como <xref:System.Type>. Clique [neste link](https://support.microsoft.com/kb/2909958/) para obter mais detalhes e exemplos de como contornar o problema.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|

