---
title: Resolução de associação tardia; poderiam ocorrer erros de tempo de execução
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 9caf02907e4b6de4c2bd8de778d4ad7a9320a82b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690573"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Resolução de associação tardia; poderiam ocorrer erros de tempo de execução
Um objeto é atribuído a uma variável declarada com o [tipo de dados do objeto](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Quando você declara uma variável como `Object`, o compilador deve executar *ligação tardia*, que faz com que operações extras em tempo de execução. Ele também expõe seu aplicativo para possíveis erros de tempo de execução. Por exemplo, se você atribuir uma <xref:System.Windows.Forms.Form> para o `Object` variável e, em seguida, tente acessar o <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> propriedade, o tempo de execução gera uma <xref:System.MemberAccessException> porque o <xref:System.Windows.Forms.Form> classe não expõe um `NameTable` propriedade.  
  
 Se você declarar a variável para ser de um tipo específico, o compilador pode executar *vinculação inicial* em tempo de compilação. Isso resulta em melhor desempenho, acesso controlado aos membros do tipo específico e melhorar a legibilidade do código.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42017  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se possível, declare a variável para ser de um tipo específico.  
  
## <a name="see-also"></a>Consulte também
- [Associação Antecipada e Tardia](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Declaração de Variável do Objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
