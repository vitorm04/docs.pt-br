---
title: Instruções 'Line' não são mais compatíveis (erro de compilador do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: c7a3e6bcd0db268a0e0acfc74c570e26f89cff6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921063"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Instruções 'Line' não são mais compatíveis (erro de compilador do Visual Basic)
Não há suporte para instruções de linha. Funcionalidade de e/s de arquivo está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e a funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.  
  
 **ID do erro:** BC30830  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2. Se executar gráficos, use `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO>
- <xref:System.Drawing>
- [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
