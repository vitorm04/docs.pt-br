---
title: Tipos de dados diversos (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2de377fa9dfd7ec13cdbb9b700f8485b0c0e2106
ms.lasthandoff: 03/13/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a>Tipos de dados diversos (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece vários tipos de dados que não estão familiarizados com números ou caracteres. Em vez disso, eles lidam com dados especializados, como Sim/não valores, valores de data/hora e endereços de objeto.  
  
 Para uma tabela que mostre uma comparação lado a lado do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="boolean-type"></a>Tipo booleano  
 O [tipo de dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) é um valor sem sinal que é interpretado como `True` ou `False`. Sua largura de dados depende da plataforma de implementação. Se uma variável pode conter apenas valores de dois estados, como verdadeiro/falso, Sim/não ou ativado/desativado, declare-o como `Boolean`.  
  
## <a name="date-type"></a>Tipo de data  
 O [tipo de dados data](../../../../visual-basic/language-reference/data-types/date-data-type.md) é um valor de 64 bits que contém informações de data e hora. Cada incremento representa 100 nanossegundos de tempo decorrido desde o início (12:00 AM) de 1º de janeiro do ano 1 no calendário gregoriano. Se uma variável pode conter um valor de data, um valor de tempo ou ambos, declare-o como `Date`.  
  
## <a name="object-type"></a>Tipo de Objeto  
 O [tipo de dados de objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md) é um endereço de 32 bits que aponta para uma instância de objeto dentro de seu aplicativo ou em algum outro aplicativo. Um `Object` variável pode referir-se a qualquer objeto que seu aplicativo reconheça, ou aos dados de qualquer tipo de dados. Isso inclui tanto *tipos de valor*, como `Integer`, `Boolean`e instâncias de estrutura e *tipos de referência*, que são instâncias de objetos criados a partir de classes, como `String` e <xref:System.Windows.Forms.Form>e instâncias de array.</xref:System.Windows.Forms.Form>  
  
 Se uma variável armazena um ponteiro para uma instância de uma classe que você não souber em tempo de compilação, ou se ele pode apontar para dados de vários tipos de dados, declare-o como `Object`.  
  
 A vantagem do `Object` é do tipo de dados que você pode usá-lo para armazenar dados de qualquer tipo de dados. A desvantagem é que você provoca operações extras que levam mais tempo de execução e fazer com que seu aplicativo execute mais lentamente. Se você usar um `Object` variável para tipos de valor, você provoca *conversão boxing* e *unboxing*. Se você usá-lo para tipos de referência, você provoca *ligação tardia*.  
  
## <a name="see-also"></a>Consulte também  
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Tipos de dados de caractere](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
