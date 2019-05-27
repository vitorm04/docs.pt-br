---
title: -codepage (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 59dc1abc3f678a4cf15543c11f9f200ff318ce8f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876922"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="654eb-102">-codepage (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="654eb-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="654eb-103">Esta opção especifica qual página de código deve ser usada durante a compilação caso a página necessária não seja a página de código padrão atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="654eb-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="654eb-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="654eb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="654eb-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="654eb-106">Especifica a ID da página de código a ser usada para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="654eb-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="654eb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="654eb-107">Remarks</span></span>  
 <span data-ttu-id="654eb-108">O compilador tentará primeiro interpretar todos os arquivos de origem como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="654eb-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="654eb-109">Se seus arquivos de código-fonte estiverem em uma codificação diferente de UTF-8 e usarem caracteres diferentes de caracteres ASCII de 7 bits, use a opção **-codepage** para especificar qual página de código deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="654eb-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="654eb-110">**-codepage** se aplica a todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="654eb-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="654eb-111">Consulte [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) para obter informações sobre como localizar quais páginas de código têm suporte do sistema.</span><span class="sxs-lookup"><span data-stu-id="654eb-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="654eb-112">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="654eb-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654eb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="654eb-113">See also</span></span>

- [<span data-ttu-id="654eb-114">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="654eb-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="654eb-115">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="654eb-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
