---
title: "Resolução de ligação tardia; poderão ocorrer erros de tempo de execução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
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
ms.openlocfilehash: 3ac885b0de2c4f44d4323487fc55cde9b23defa4
ms.lasthandoff: 03/13/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Resolução de associação tardia; poderiam ocorrer erros de tempo de execução
Um objeto é atribuído a uma variável declarada com o [tipo de dados do objeto](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Ao declarar uma variável como `Object`, o compilador deve executar *ligação tardia*, que causa operações extras em tempo de execução. Ele também expõe sua aplicação a potenciais erros em tempo de execução. Por exemplo, se você atribuir um <xref:System.Windows.Forms.Form>para o `Object` variável e, em seguida, tente acessar o <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>propriedade, o tempo de execução gera um <xref:System.MemberAccessException>porque o <xref:System.Windows.Forms.Form>classe expõe um `NameTable` propriedade.</xref:System.Windows.Forms.Form> </xref:System.MemberAccessException> </xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> </xref:System.Windows.Forms.Form>  
  
 Se você declarar a variável para ser de um tipo específico, o compilador pode executar *vinculação inicial* em tempo de compilação. Isso resulta em melhor desempenho, acesso controlado aos membros do tipo específico e melhor legibilidade do seu código.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42017  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se possível, declare a variável para ser de um tipo específico.  
  
## <a name="see-also"></a>Consulte também  
 [Associação antecipada e tardia](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [Declaração de Variável do Objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
