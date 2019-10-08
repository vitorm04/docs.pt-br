---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: df05ff6caeae2fb2db6a8d7c8fec1b81774a9fa4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005380"
---
# <a name="-nowin32manifest-visual-basic"></a>-nowin32manifest (Visual Basic)
Instrui o compilador a não inserir nenhum manifesto de aplicativo no arquivo executável.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Comentários  
 Quando essa opção for usada, o aplicativo estará sujeito à virtualização no Windows Vista, a menos que você forneça um manifesto do aplicativo em um arquivo de recurso Win32 ou durante uma etapa de build posterior. Para saber mais sobre virtualização, confira [Implantação do ClickOnce no Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Para saber mais sobre a criação do manifesto, confira [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
