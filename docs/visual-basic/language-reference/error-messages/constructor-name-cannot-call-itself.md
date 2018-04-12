---
title: Construtor &#39; &lt;nome&gt;&#39; não é possível chamar a mesmo
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Construtor &#39; &lt;nome&gt;&#39; não é possível chamar a mesmo
Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.  
  
 A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ele é o primeiro criado. Uma classe ou estrutura pode ter vários construtores, contanto que todos tenham listas de parâmetros diferentes. Um construtor pode chamar outro construtor para executar sua funcionalidade além de seu próprio. Mas não faz sentido um construtor chamar a mesmo e de fato resultaria em recursão infinita se permitido.  
  
 **ID do erro:** BC30298  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a lista de parâmetro do construtor sendo chamado. Ele deve ser diferente do construtor fazendo a chamada.  
  
2.  Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.  
  
## <a name="see-also"></a>Consulte também  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
