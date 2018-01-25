---
title: "-nowin32manifest (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7682a3e1ecf483b8495d817ef01e57093ae0f987
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="4bb9b-102">-nowin32manifest (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="4bb9b-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="4bb9b-103">Use a opção **-nowin32manifest** para instruir o compilador a não inserir nenhum manifesto do aplicativo no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="4bb9b-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bb9b-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="4bb9b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bb9b-105">Remarks</span></span>  
 <span data-ttu-id="4bb9b-106">Quando essa opção for usada, o aplicativo estará sujeito à virtualização no Windows Vista, a menos que você forneça um manifesto do aplicativo em um arquivo de recurso Win32 ou durante uma etapa de build posterior.</span><span class="sxs-lookup"><span data-stu-id="4bb9b-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="4bb9b-107">No Visual Studio, defina essa opção na página **Propriedade do Aplicativo** selecionando a opção **Criar aplicativo sem um manifesto** na lista suspensa **Manifesto**.</span><span class="sxs-lookup"><span data-stu-id="4bb9b-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="4bb9b-108">Para obter mais informações, consulte [Página Aplicativo, Designer de Projeto (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="4bb9b-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="4bb9b-109">Para obter mais informações sobre a criação do manifesto, consulte [-win32manifest (Opções do compilador do C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4bb9b-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb9b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bb9b-110">See Also</span></span>  
 [<span data-ttu-id="4bb9b-111">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="4bb9b-111">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4bb9b-112">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="4bb9b-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
