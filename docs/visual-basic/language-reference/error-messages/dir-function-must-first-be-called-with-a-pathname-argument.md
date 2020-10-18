---
title: A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 7f8191b0ef5452fcf6f3a20c3e0f28ca84ef9c4a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163422"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'

Uma chamada inicial para a `Dir` função não inclui o `PathName` argumento. A primeira chamada para `Dir` deve incluir uma `PathName` , mas as chamadas subsequentes para não `Dir` precisam incluir parâmetros para recuperar o próximo item.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Forneça um `PathName` argumento na chamada de função.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
