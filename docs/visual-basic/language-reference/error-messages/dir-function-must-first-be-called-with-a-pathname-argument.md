---
title: '&#39; Dir &#39; função deve ser chamada primeiro com um &#39; Caminho &#39; argumento'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39; Dir &#39; função deve ser chamada primeiro com um &#39; Caminho &#39; argumento
Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento. A primeira chamada para `Dir` deve incluir um `PathName`, mas subsequentes chamadas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Forneça um `PathName` argumento na chamada de função.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
