---
title: "Convers&#245;es entre cadeias de caracteres e outros tipos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversões,   (tipo de dados)"
  - "conversões, Tipo "
  - "conversão de tipo de dados, string"
  - "opções regionais"
  - "conversão de cadeia de caracteres"
  - "conversão de tipo, string"
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Convers&#245;es entre cadeias de caracteres e outros tipos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode converter um numérico, `Boolean`, ou valor de data\/hora um `String`.  Você também pode converter na direção contrária — a partir de um valor de seqüência de caracteres numéricos, `Boolean`, ou `Date` — desde que o conteúdo da seqüência de caracteres pode ser interpretado como um valor válido de tipo de dados de destino.  Em caso negativo, ocorrerá um erro de tempo de execução.  
  
 As conversões para todas as essas atribuições, em qualquer direção, são restringir conversões.  You should use the type conversion keywords \(`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`\).  O <xref:Microsoft.VisualBasic.Strings.Format%2A> e <xref:Microsoft.VisualBasic.Conversion.Val%2A> funções fornecem controle adicional sobre conversões entre cadeias de caracteres e números.  
  
 Se você tiver definido uma classe ou estrutura, você pode definir os operadores de conversão de tipo entre `String` e o tipo de sua classe ou estrutura.  Para obter mais informações, consulte [Como definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## Conversão de números em seqüências de caracteres  
 Você pode usar o `Format` função para converter um número em uma seqüência de caracteres formatada, que pode incluir não apenas os dígitos apropriados, mas também a formatação de símbolos, como um sinal de moeda \(como `$`\), milhares separadores ou  *os símbolos de agrupamento de dígitos* \(como `,`\) e um separador decimal \(como `.`\).  `Format`utiliza automaticamente os símbolos corretos de acordo com o  **Opções regionais** as configurações especificadas no Windows  **Painel de controle**.  
  
 Observe que a concatenação \(`&`\) operador pode converter um número em uma seqüência de caracteres implicitamente, como mostra o exemplo a seguir.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## Conversão de seqüências de caracteres em números  
 Você pode usar o `Val` função explicitamente converter os dígitos em uma seqüência de caracteres para um número.  `Val`lê a seqüência de caracteres até encontrar um caractere diferente de um dígito, espaço, guia, alimentação de linha ou período.  As seqüências "e O" e "& H" alterar a base do sistema numérico e encerrar a varredura.  Até que ela pare de leitura, `Val` converte todos os caracteres apropriados em um valor numérico.  Por exemplo, a instrução a seguir retorna o valor `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Quando [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte uma seqüência de caracteres em um valor numérico, ele usa o  **Opções regionais** as configurações especificadas no Windows  **Painel de controle** para interpretar os milhares separador, o separador decimal e o símbolo de moeda.  Isso significa que uma conversão pode ter êxito em uma configuração, mas não um outro.  Por exemplo, `"$14.20"` é aceitável na localidade Inglês \(Estados Unidos\), mas não em qualquer localidade francês.  
  
## Consulte também  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Como converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Introdução a aplicativos internacionais com base no .NET Framework](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)