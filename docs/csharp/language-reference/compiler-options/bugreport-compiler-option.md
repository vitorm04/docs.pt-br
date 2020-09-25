---
description: -bugreport (opções do compilador C#)
title: -bugreport (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 2afab44eec0c7bcc9809b458be0348093cb6dd07
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196813"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="f39b3-103">-bugreport (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="f39b3-103">-bugreport (C# Compiler Options)</span></span>

<span data-ttu-id="f39b3-104">Especifica que as informações de depuração devem ser colocadas em um arquivo para análise posterior.</span><span class="sxs-lookup"><span data-stu-id="f39b3-104">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39b3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f39b3-105">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f39b3-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f39b3-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="f39b3-107">O nome do arquivo que conterá o relatório de bug.</span><span class="sxs-lookup"><span data-stu-id="f39b3-107">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f39b3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f39b3-108">Remarks</span></span>  

 <span data-ttu-id="f39b3-109">A opção **-bugreport** especifica que as informações a seguir devem ser colocadas em `file`:</span><span class="sxs-lookup"><span data-stu-id="f39b3-109">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="f39b3-110">Uma cópia de todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="f39b3-110">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="f39b3-111">Uma lista das opção do compilador usadas na compilação.</span><span class="sxs-lookup"><span data-stu-id="f39b3-111">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="f39b3-112">Informações de versão sobre o compilador, o tempo de execução e o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f39b3-112">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="f39b3-113">Assemblies e módulos referenciados, salvos como dígitos hexadecimais, exceto os assemblies que vêm com o .NET Framework e o SDK.</span><span class="sxs-lookup"><span data-stu-id="f39b3-113">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="f39b3-114">Saída do compilador, se houver.</span><span class="sxs-lookup"><span data-stu-id="f39b3-114">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="f39b3-115">Uma solicitação de descrição do problema.</span><span class="sxs-lookup"><span data-stu-id="f39b3-115">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="f39b3-116">Uma solicitação de como você acha que o problema deve ser corrigido.</span><span class="sxs-lookup"><span data-stu-id="f39b3-116">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="f39b3-117">Se essa opção for usada com **-errorreport:prompt** ou **-errorreport:send**, as informações no arquivo serão enviadas à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="f39b3-117">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="f39b3-118">Como uma cópia de todos os arquivos de código-fonte será colocada no `file`, talvez seja desejável reproduzir o suposto defeito do código no programa mais curto possível.</span><span class="sxs-lookup"><span data-stu-id="f39b3-118">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="f39b3-119">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="f39b3-119">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="f39b3-120">Observe que os conteúdos do arquivo gerado expõem o código-fonte, o que pode resultar na divulgação acidental de informações.</span><span class="sxs-lookup"><span data-stu-id="f39b3-120">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39b3-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="f39b3-121">See also</span></span>

- [<span data-ttu-id="f39b3-122">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="f39b3-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f39b3-123">-ERRORREPORT (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="f39b3-123">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="f39b3-124">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="f39b3-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
