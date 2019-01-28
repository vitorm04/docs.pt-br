---
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
ms.openlocfilehash: 8d28ef1334df847865721783fa98aaa9d8c576be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528570"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="a3ff2-102">-noconfig (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="a3ff2-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="a3ff2-103">A opção **-noconfig** informa que o compilador não deve compilar com o arquivo csc.rsp, localizado no mesmo diretório que o arquivo csc.exe e carregado dele.</span><span class="sxs-lookup"><span data-stu-id="a3ff2-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ff2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3ff2-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3ff2-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3ff2-105">Remarks</span></span>  
 <span data-ttu-id="a3ff2-106">O arquivo csc.rsp referencia todos os assemblies que acompanham o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3ff2-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="a3ff2-107">As referências reais que o ambiente de desenvolvimento do Visual Studio .NET inclui dependem do tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="a3ff2-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="a3ff2-108">É possível modificar o arquivo csc.rsp e especificar opções do compilador adicionais que devem ser incluídas em cada compilação na linha de comando com csc.exe (exceto a opção **-noconfig**).</span><span class="sxs-lookup"><span data-stu-id="a3ff2-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="a3ff2-109">O compilador processa as opções passadas para o comando **csc** pela última vez.</span><span class="sxs-lookup"><span data-stu-id="a3ff2-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="a3ff2-110">Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a3ff2-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="a3ff2-111">Se você não desejar que o compilador procure e use as configurações no arquivo csc.rsp, especifique **-noconfig**.</span><span class="sxs-lookup"><span data-stu-id="a3ff2-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="a3ff2-112">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="a3ff2-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ff2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3ff2-113">See also</span></span>

- [<span data-ttu-id="a3ff2-114">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="a3ff2-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="a3ff2-115">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="a3ff2-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
