---
title: "Informa&#231;&#245;es do chamador (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Informa&#231;&#245;es do chamador (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usando atributos de informações do chamador, você pode obter informações sobre o chamador de um método. Você pode obter o caminho do arquivo do código\-fonte, o número da linha no código\-fonte e o nome do membro do chamador. Essas informações são úteis para rastreamento, depuração e criação de ferramentas de diagnóstico.  
  
 Para obter essas informações, você deve usar os atributos que são aplicados aos parâmetros opcionais, cada um deles tem um valor padrão. A tabela a seguir lista os atributos de informações do chamador que são definidos na <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:  
  
||||  
|-|-|-|  
|Atributo|Descrição|Tipo|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Caminho completo do arquivo de origem que contém o chamador. Este é o caminho de arquivo em tempo de compilação.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Número da linha no arquivo de origem no qual o método é chamado.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nome de método ou propriedade do chamador. Consulte [Nomes de membro](#MEMBERNAMES) mais adiante neste tópico.|`String`|  
  
## Exemplo  
 O exemplo a seguir mostra como usar atributos de informações do chamador. Em cada chamada para o `TraceMessage` método, as informações do chamador é substituído como argumentos para os parâmetros opcionais.  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## Comentários  
 Você deve especificar um valor padrão explícito para cada parâmetro opcional. Você não pode aplicar atributos de informações do chamador aos parâmetros que não são especificados como opcionais.  
  
 Os atributos de informações do chamador não tornam um parâmetro opcional. Em vez disso, eles afetam o valor padrão que é passado quando o argumento for omitido.  
  
 Os valores de informações do chamador são emitidos como literais para a linguagem intermediária \(IL\) em tempo de compilação. Ao contrário dos resultados do <xref:System.Exception.StackTrace%2A> propriedade para exceções, os resultados não são afetados por ofuscamento.  
  
 Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá\-las.  
  
###  <a name="MEMBERNAMES"></a> Nomes de membro  
 Você pode usar o `CallerMemberName` atributo Evite especificar o nome do membro como um `String` argumento para o método chamado. Usando essa técnica, você pode evitar o problema que **refatoração Renomear** não altera o `String` valores. Esse benefício é especialmente útil para as seguintes tarefas:  
  
-   Usando rotinas de rastreamento e diagnóstico.  
  
-   Implementando o <xref:System.ComponentModel.INotifyPropertyChanged> ao associar dados da interface. Essa interface permite que a propriedade de um objeto para notificar um controle ligado a propriedade foi alterada, para que o controle pode exibir as informações atualizadas. Sem o `CallerMemberName` atributo, você deve especificar o nome da propriedade como um literal.  
  
 O gráfico a seguir mostra o membro nomes que são retornados quando você usa o `CallerMemberName` atributo.  
  
|As chamadas ocorrem em|Resultado de nome de membro|  
|----------------------------|---------------------------------|  
|Método, propriedade ou evento|O nome do método, propriedade ou evento que originou a chamada.|  
|Construtor|A cadeia de caracteres ". ctor"|  
|Construtor estático|A cadeia de caracteres ". cctor"|  
|Destruidor|A cadeia de caracteres "Finalize"|  
|Operadores definidos pelo usuário ou conversões|O nome gerado para o membro, por exemplo, "op\_Addition".|  
|Construtor de atributo|O nome do membro ao qual o atributo é aplicado. Se o atributo é qualquer elemento em um membro \(como um parâmetro, um valor de retorno ou um parâmetro de tipo genérico\), esse resultado é o nome do membro que está associado a esse elemento.|  
|Nenhum membro contentor \(por exemplo, nível de assembly ou atributos que são aplicados aos tipos\)|O valor padrão do parâmetro opcional.|  
  
## Consulte também  
 [Atributos](../../../visual-basic/language-reference/attributes.md)   
 [Atributos comuns \(Visual Basic\)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)   
 [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Conceitos de programação \(Visual Basic\)](../../../visual-basic/programming-guide/concepts/index.md)