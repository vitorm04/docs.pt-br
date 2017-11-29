---
title: "Segurança e campos de matriz públicos somente leitura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae2e9a7dd9e08344c254b52c7139c6d1dd2776a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="abda8-102">Segurança e campos de matriz públicos somente leitura</span><span class="sxs-lookup"><span data-stu-id="abda8-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="abda8-103">Nunca use campos de matriz públicos somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança de seus aplicativos, como campos de matriz públicos somente leitura podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="abda8-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abda8-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="abda8-104">Remarks</span></span>  
 <span data-ttu-id="abda8-105">Algumas classes do .NET framework incluem campos públicos somente leitura que contêm parâmetros de limite específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="abda8-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="abda8-106">Por exemplo, o <xref:System.IO.Path.InvalidPathChars> campo é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="abda8-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="abda8-107">Muitos campos semelhantes estão presentes no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abda8-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="abda8-108">Os valores dos campos públicos somente leitura, como <xref:System.IO.Path.InvalidPathChars> pode ser modificado por seu código ou o código que compartilha o domínio de aplicativo do seu código.</span><span class="sxs-lookup"><span data-stu-id="abda8-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="abda8-109">Você não deve usar campos de matriz públicos somente leitura como este para definir o comportamento de limite de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="abda8-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="abda8-110">Se você fizer isso, código mal-intencionado pode alterar as definições de limite e usem o seu código de maneiras inesperadas.</span><span class="sxs-lookup"><span data-stu-id="abda8-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="abda8-111">Na versão 2.0 e posterior do .NET Framework, você deve usar os métodos que retornam uma nova matriz em vez de usar campos de matriz públicos.</span><span class="sxs-lookup"><span data-stu-id="abda8-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="abda8-112">Por exemplo, em vez de usar o <xref:System.IO.Path.InvalidPathChars> campo, você deve usar o <xref:System.IO.Path.GetInvalidPathChars%2A> método.</span><span class="sxs-lookup"><span data-stu-id="abda8-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="abda8-113">Observe que os tipos do .NET Framework não usam os campos públicos para definir tipos de limite internamente.</span><span class="sxs-lookup"><span data-stu-id="abda8-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="abda8-114">Em vez disso, o .NET Framework usa campos particulares separados.</span><span class="sxs-lookup"><span data-stu-id="abda8-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="abda8-115">Alterando os valores desses campos públicos não altera o comportamento de tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abda8-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abda8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abda8-116">See Also</span></span>  
 [<span data-ttu-id="abda8-117">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="abda8-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
