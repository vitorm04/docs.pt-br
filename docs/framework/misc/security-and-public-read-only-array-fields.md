---
title: Segurança e campos de matriz públicos somente leitura
description: Leia por que você deve evitar o uso de campos públicos de matriz somente leitura para definir o comportamento de limite ou a segurança de seus aplicativos.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 5e499f8052306cd1ad063c9f44a2a0f1d0b365ef
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855732"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="e958f-103">Segurança e campos de matriz públicos somente leitura</span><span class="sxs-lookup"><span data-stu-id="e958f-103">Security and Public Read-only Array Fields</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="e958f-104">Nunca use campos de matriz pública somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança de seus aplicativos porque campos de matriz pública somente leitura podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="e958f-104">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e958f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e958f-105">Remarks</span></span>  

<span data-ttu-id="e958f-106">Algumas classes .NET incluem campos públicos somente leitura que contêm parâmetros de limite específicos da plataforma.</span><span class="sxs-lookup"><span data-stu-id="e958f-106">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="e958f-107">Por exemplo, o <xref:System.IO.Path.InvalidPathChars> campo é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="e958f-107">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="e958f-108">Muitos campos semelhantes estão presentes em todo o .NET.</span><span class="sxs-lookup"><span data-stu-id="e958f-108">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="e958f-109">Os valores de campos somente leitura públicos como <xref:System.IO.Path.InvalidPathChars> podem ser modificados pelo código ou código que compartilha o domínio do aplicativo do código.</span><span class="sxs-lookup"><span data-stu-id="e958f-109">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="e958f-110">Você não deve usar campos de matriz pública somente leitura como este para definir o comportamento de limite de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e958f-110">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="e958f-111">Se você fizer isso, o código mal-intencionado poderá alterar as definições de limite e usar seu código de maneiras inesperadas.</span><span class="sxs-lookup"><span data-stu-id="e958f-111">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="e958f-112">Na versão 2,0 e posteriores do .NET Framework, você deve usar métodos que retornam uma nova matriz em vez de campos de matriz pública.</span><span class="sxs-lookup"><span data-stu-id="e958f-112">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="e958f-113">Por exemplo, em vez de usar o <xref:System.IO.Path.InvalidPathChars> campo, você deve usar o <xref:System.IO.Path.GetInvalidPathChars%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e958f-113">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="e958f-114">Observe que os tipos de .NET Framework não usam os campos públicos para definir tipos de limite internamente.</span><span class="sxs-lookup"><span data-stu-id="e958f-114">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="e958f-115">Em vez disso, o .NET Framework usa campos particulares separados.</span><span class="sxs-lookup"><span data-stu-id="e958f-115">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="e958f-116">A alteração dos valores desses campos públicos não altera o comportamento dos tipos de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e958f-116">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e958f-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="e958f-117">See also</span></span>

- [<span data-ttu-id="e958f-118">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="e958f-118">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
