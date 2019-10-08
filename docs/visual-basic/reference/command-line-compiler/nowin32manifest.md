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
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="94cf3-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94cf3-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="94cf3-103">Instrui o compilador a não inserir nenhum manifesto de aplicativo no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="94cf3-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94cf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94cf3-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="94cf3-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="94cf3-105">Remarks</span></span>  
 <span data-ttu-id="94cf3-106">Quando essa opção for usada, o aplicativo estará sujeito à virtualização no Windows Vista, a menos que você forneça um manifesto do aplicativo em um arquivo de recurso Win32 ou durante uma etapa de build posterior.</span><span class="sxs-lookup"><span data-stu-id="94cf3-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="94cf3-107">Para saber mais sobre virtualização, confira [Implantação do ClickOnce no Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="94cf3-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="94cf3-108">Para saber mais sobre a criação do manifesto, confira [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="94cf3-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94cf3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94cf3-109">See also</span></span>

- [<span data-ttu-id="94cf3-110">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94cf3-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="94cf3-111">Página de Aplicativo, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94cf3-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
