---
title: A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282576"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento. A primeira chamada para `Dir` deve incluir uma `PathName`, as chamadas subsequentes, mas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Forneça um `PathName` argumento na chamada de função.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
