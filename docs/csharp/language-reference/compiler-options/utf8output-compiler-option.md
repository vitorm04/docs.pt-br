---
title: "-utf8output (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /utf8output
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3716445cb779e98f777a1677ff67e1ba603c5fa2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-utf8output-c-compiler-options"></a><span data-ttu-id="e7aed-102">-utf8output (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="e7aed-102">-utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="e7aed-103">A opção **-utf8output** exibe a saída do compilador usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e7aed-103">The **-utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7aed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7aed-104">Syntax</span></span>  
  
```console  
-utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="e7aed-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7aed-105">Remarks</span></span>  
 <span data-ttu-id="e7aed-106">Em algumas configurações internacionais, a saída do compilador não pode ser exibida corretamente no console.</span><span class="sxs-lookup"><span data-stu-id="e7aed-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="e7aed-107">Nessas configurações, use **-utf8output** e redirecione a saída do compilador para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e7aed-107">In these configurations, use **-utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="e7aed-108">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="e7aed-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7aed-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7aed-109">See Also</span></span>  
 [<span data-ttu-id="e7aed-110">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="e7aed-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
