---
title: "&#39; Linha &#39; instruções não são mais suportados (erro de compilador do Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords: BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d2db5dc786749360dfcf6789f12b5659d5713fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39; Linha &#39; instruções não são mais suportados (erro de compilador do Visual Basic)
Não há suporte para instruções de linha. A funcionalidade de e/s de arquivo está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.  
  
 **ID do erro:** BC30830  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Se estiver executando o gráfico, use `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
