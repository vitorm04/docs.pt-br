---
title: A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874455"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'

Uma chamada inicial para a `Dir` função não inclui o `PathName` argumento. A primeira chamada para `Dir` deve incluir uma `PathName` , mas as chamadas subsequentes para não `Dir` precisam incluir parâmetros para recuperar o próximo item.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Forneça um `PathName` argumento na chamada de função.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
