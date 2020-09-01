---
description: -nowin32manifest (opções do compilador C#)
title: -nowin32manifest (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8514ab5b118e320d456d1b7367fab3b463c3607a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125053"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="922f7-103">-nowin32manifest (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="922f7-103">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="922f7-104">Use a opção **-nowin32manifest** para instruir o compilador a não inserir nenhum manifesto do aplicativo no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="922f7-104">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922f7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="922f7-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="922f7-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="922f7-106">Remarks</span></span>  
 <span data-ttu-id="922f7-107">Quando essa opção for usada, o aplicativo estará sujeito à virtualização no Windows Vista, a menos que você forneça um manifesto do aplicativo em um arquivo de recurso Win32 ou durante uma etapa de build posterior.</span><span class="sxs-lookup"><span data-stu-id="922f7-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="922f7-108">No Visual Studio, defina essa opção na página **Propriedade do Aplicativo** selecionando a opção **Criar aplicativo sem um manifesto** na lista suspensa **Manifesto**.</span><span class="sxs-lookup"><span data-stu-id="922f7-108">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="922f7-109">Para obter mais informações, consulte [página do aplicativo, designer de projeto (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="922f7-109">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="922f7-110">Para obter mais informações sobre a criação do manifesto, consulte [-win32manifest (Opções do compilador do C#)](./win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="922f7-110">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="922f7-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="922f7-111">See also</span></span>

- [<span data-ttu-id="922f7-112">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="922f7-112">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="922f7-113">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="922f7-113">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
