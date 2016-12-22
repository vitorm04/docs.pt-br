---
title: "Convers&#245;es impl&#237;citas e expl&#237;citas (Visual Basic) | Microsoft Docs"
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
  - "conversão"
  - "conversão, tipos de dados"
  - "alterando tipos de dados"
  - "conversões"
  - "conversões,   (tipo de dados)"
  - "conversões, explicit"
  - "conversões, implícito"
  - "conversões, Tipo "
  - "Função CType, conversões"
  - "conversão de tipo de dados, explicit"
  - "conversão de tipo de dados, implícito"
  - "tipos de dados [Visual Basic], conversão"
  - "conversões de tipo de dados explícitos"
  - "conversões implícitas de tipo de dados"
  - "conversão de tipo, conversões explícitas"
  - "conversão de tipo, conversões implícitas"
  - "variáveis [Visual Basic], alterando tipo de dados"
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Convers&#245;es impl&#237;citas e expl&#237;citas (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma *conversão implícita* não requer qualquer síntaxe especial no código fonte.  No exemplo a seguir, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] implicitamente converte o valor de `k` em um valor de ponto flutuante antes designá\-lo a `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 Uma *conversão explícita* usa uma palavra\-chave para a conversão de tipos.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece palavras\-vários tal chave, que forçar uma expressão entre parênteses para o tipo de dados desejados.  Essas palavras\-chave atuam como funções, mas o compilador gera o código embutido, portanto execução é ligeiramente mais rápido do que com um chamada de função.  
  
 Na seguinte extensão do exemplo anterior, a  palavra\-chave `CInt` converte o valor de `q` novamente como um número inteiro antes de atribuí\-lo para `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## Palavras\-chave conversão  
 A tabela a seguir mostra as palavras\-chave conversão disponível.  
  
||||  
|-|-|-|  
|Palavra\-chave conversão tipo|Converte uma expressão em tipo de dados|Tipos de dados permitido de expressão a ser convertido|  
|`CBool`|[Tipo de dados booliano](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `String`, `Object`|  
|`CByte`|[Tipo de dados Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Qualquer tipo numérico \(incluindo `SByte`, `Boolean` e os tipos enumerados\), `String`, `Object`|  
|`CChar`|[Tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Tipo de dados Data](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Tipo de dados double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CDec`|[Tipo de dados decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CInt`|[Tipo de dados inteiro](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CLng`|[Tipo de dados Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CObj`|[Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer tipo|  
|`CSByte`|[Tipo de dados SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `Boolean` e os tipos enumerados\), `String`, `Object`|  
|`CShort`|[Tipo de dados curto](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CSng`|[Tipo de dados único](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CStr`|[Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `Char`,matriz `Char`,`Date`,`Object`|  
|`CType`|Tipo especificado após a vírgula \(`,`\)|Ao converter para um *Tipo de dados elementar* \(incluindo uma matriz de um tipo elementar\) os mesmos tipos como permitido para a palavra\-chave conversão correspondente<br /><br /> Ao converter em interfaces um *tipo de dados composto*, o ele implementa e as classes do qual ele herda<br /><br /> Ao converter a uma classe ou estrutura na qual você tenha sobrecarregado `CType`, que classe ou estrutura|  
|`CUInt`|[Tipo de dados UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CULng`|[Tipo de dados ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
|`CUShort`|[Tipo de dados UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Qualquer tipo numérico \(incluindo `Byte`, `SByte` e os tipos enumerados\), `Boolean`, `String`,`Object`|  
  
## A função CType  
 O [Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) opera em dois argumentos.  A primeira é a expressão a ser convertido, e o segundo é a classe tipo ou objeto de dados de destino.  Observe que o primeiro argumento deve ser uma expressão, não um tipo.  
  
 `CType` é uma   *função in\-line*, que significa que o código compilado faz a conversão, com frequência sem gerar um chamada de função.  Isso melhora o desempenho.  
  
 Para uma comparação de `CType` com as outras conversão de tipos palavras\-chave, consulte [Operador DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) e [Operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### Tipos elementar  
 O exemplo a seguir demonstra o uso de `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### Tipos Composite  
 Você pode usar `CType` para converter valores em tipos de dados compostos bem como para tipos elementares.  Também pode usá\-lo para forçar uma classe de objeto para o tipo de uma das suas interfaces, como no exemplo a seguir.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### Tipos de matriz  
 `CType` também pode converter tipos de dados de matriz, como no exemplo a seguir.  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 Para mais informações e um exemplo, consulte [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).  
  
### Tipos definindo CType  
 Você pode definir `CType` em uma classe ou estrutura que você definiu.  Isso permite que você para converter valores de e para o tipo de sua classe ou estrutura.  Para mais informações e um exemplo, consulte [Como definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Valores usados com uma palavra\-chave conversão deve ser válido para o tipo de dados de destino, ou ocorrerá um erro.  Por exemplo, se você tentar converter um `Long` em um `Integer`,o valor de `Long` deve ser dentro do intervalo válido para o tipo de dados `Integer`.  
  
> [!CAUTION]
>  Especificando `CType` para converter de um tipo de classe para outra falha no tempo de execução se o tipo de origem não é derivado do tipo de destino.  Uma falha gera uma exceção <xref:System.InvalidCastException>.  
  
 No entanto, se um dos tipos for uma classe ou estrutura que você definiu, e se você tiver definido `CType` nessa classe ou estrutura, uma conversão pode terá êxito se ele satisfaz os requisitos de seu `CType`.  Consulte [Como definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Executar uma conversão explícita é também conhecido como *Elenco* uma expressão a uma classe tipo ou objeto de dados especificados.  
  
## Consulte também  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Como converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)