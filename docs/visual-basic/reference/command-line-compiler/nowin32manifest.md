---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c539f7833c86215a1b0f8102f9fc46419636bc7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-nowin32manifest-visual-basic"></a>-nowin32manifest (Visual Basic)
Instrui o compilador não inserir qualquer manifesto de aplicativo para o arquivo executável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Comentários  
 Quando essa opção for usada, o aplicativo estará sujeito à virtualização no Windows Vista, a menos que você forneça um manifesto do aplicativo em um arquivo de recurso Win32 ou durante uma etapa de build posterior. Para obter mais informações sobre a virtualização, consulte [a implantação do ClickOnce no Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Para obter mais informações sobre a criação de manifesto, consulte [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
