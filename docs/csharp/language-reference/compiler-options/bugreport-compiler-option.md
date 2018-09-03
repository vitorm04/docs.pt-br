---
title: -bugreport (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 6e4674acd2a5edbbffd2babf130d2078019ab9b7
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331729"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="94131-102">-bugreport (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="94131-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="94131-103">Especifica que as informações de depuração devem ser colocadas em um arquivo para análise posterior.</span><span class="sxs-lookup"><span data-stu-id="94131-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94131-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94131-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="94131-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="94131-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="94131-106">O nome do arquivo que conterá o relatório de bug.</span><span class="sxs-lookup"><span data-stu-id="94131-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94131-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="94131-107">Remarks</span></span>  
 <span data-ttu-id="94131-108">A opção **-bugreport** especifica que as informações a seguir devem ser colocadas em `file`:</span><span class="sxs-lookup"><span data-stu-id="94131-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
-   <span data-ttu-id="94131-109">Uma cópia de todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="94131-109">A copy of all source code files in the compilation.</span></span>  
  
-   <span data-ttu-id="94131-110">Uma lista das opção do compilador usadas na compilação.</span><span class="sxs-lookup"><span data-stu-id="94131-110">A listing of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="94131-111">Informações de versão sobre o compilador, o tempo de execução e o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="94131-111">Version information about your compiler, run time, and operating system.</span></span>  
  
-   <span data-ttu-id="94131-112">Assemblies e módulos referenciados, salvos como dígitos hexadecimais, exceto os assemblies que vêm com o .NET Framework e o SDK.</span><span class="sxs-lookup"><span data-stu-id="94131-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
-   <span data-ttu-id="94131-113">Saída do compilador, se houver.</span><span class="sxs-lookup"><span data-stu-id="94131-113">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="94131-114">Uma solicitação de descrição do problema.</span><span class="sxs-lookup"><span data-stu-id="94131-114">A description of the problem, which you will be prompted for.</span></span>  
  
-   <span data-ttu-id="94131-115">Uma solicitação de como você acha que o problema deve ser corrigido.</span><span class="sxs-lookup"><span data-stu-id="94131-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="94131-116">Se essa opção for usada com **-errorreport:prompt** ou **-errorreport:send**, as informações no arquivo serão enviadas à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="94131-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="94131-117">Como uma cópia de todos os arquivos de código-fonte será colocada no `file`, talvez seja desejável reproduzir o suposto defeito do código no programa mais curto possível.</span><span class="sxs-lookup"><span data-stu-id="94131-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="94131-118">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="94131-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="94131-119">Observe que os conteúdos do arquivo gerado expõem o código-fonte, o que pode resultar na divulgação acidental de informações.</span><span class="sxs-lookup"><span data-stu-id="94131-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94131-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94131-120">See Also</span></span>  

- [<span data-ttu-id="94131-121">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="94131-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="94131-122">-errorreport (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="94131-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
- [<span data-ttu-id="94131-123">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="94131-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
