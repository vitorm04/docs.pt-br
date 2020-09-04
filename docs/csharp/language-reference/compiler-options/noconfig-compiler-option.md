---
description: -noconfig (opções do compilador C#)
title: -noconfig (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 677b96df8c6686e46c0db93eabe72dd483b947e4
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466060"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="dae2d-103">-noconfig (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="dae2d-103">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="dae2d-104">A opção **-noconfig** informa que o compilador não deve compilar com o arquivo csc.rsp, localizado no mesmo diretório que o arquivo csc.exe e carregado dele.</span><span class="sxs-lookup"><span data-stu-id="dae2d-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae2d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dae2d-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="dae2d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="dae2d-106">Remarks</span></span>  
 <span data-ttu-id="dae2d-107">O arquivo csc. rsp faz referência a todos os assemblies fornecidos com .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dae2d-107">The csc.rsp file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="dae2d-108">As referências reais que o ambiente de desenvolvimento do Visual Studio .NET inclui dependem do tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="dae2d-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="dae2d-109">Você pode modificar o arquivo csc. rsp e especificar opções de compilador adicionais que devem ser incluídas em todas as compilações da linha de comando com csc.exe (exceto a opção **-noconfig** ).</span><span class="sxs-lookup"><span data-stu-id="dae2d-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="dae2d-110">O compilador processa as opções passadas para o comando **csc** pela última vez.</span><span class="sxs-lookup"><span data-stu-id="dae2d-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="dae2d-111">Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="dae2d-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="dae2d-112">Se você não desejar que o compilador procure e use as configurações no arquivo csc.rsp, especifique **-noconfig**.</span><span class="sxs-lookup"><span data-stu-id="dae2d-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="dae2d-113">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="dae2d-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae2d-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="dae2d-114">See also</span></span>

- [<span data-ttu-id="dae2d-115">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="dae2d-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dae2d-116">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="dae2d-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
