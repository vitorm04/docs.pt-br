---
title: Segurança e campos de matriz públicos somente leitura
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 215e8136b4bc3f2982cdb2d8382b0eca6a881f9b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217042"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="04f90-102">Segurança e campos de matriz públicos somente leitura</span><span class="sxs-lookup"><span data-stu-id="04f90-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="04f90-103">Nunca use campos de matriz pública somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança de seus aplicativos porque campos de matriz pública somente leitura podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="04f90-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04f90-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="04f90-104">Remarks</span></span>  
 <span data-ttu-id="04f90-105">Algumas classes do .NET Framework incluem campos públicos somente leitura que contêm parâmetros de limite específicos da plataforma.</span><span class="sxs-lookup"><span data-stu-id="04f90-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="04f90-106">Por exemplo, o campo <xref:System.IO.Path.InvalidPathChars> é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="04f90-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="04f90-107">Muitos campos semelhantes estão presentes durante o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04f90-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="04f90-108">Os valores de campos somente leitura públicos como <xref:System.IO.Path.InvalidPathChars> podem ser modificados pelo código ou código que compartilha o domínio do aplicativo do seu código.</span><span class="sxs-lookup"><span data-stu-id="04f90-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="04f90-109">Você não deve usar campos de matriz pública somente leitura como este para definir o comportamento de limite de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="04f90-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="04f90-110">Se você fizer isso, o código mal-intencionado poderá alterar as definições de limite e usar seu código de maneiras inesperadas.</span><span class="sxs-lookup"><span data-stu-id="04f90-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="04f90-111">Na versão 2,0 e posteriores do .NET Framework, você deve usar métodos que retornam uma nova matriz em vez de campos de matriz pública.</span><span class="sxs-lookup"><span data-stu-id="04f90-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="04f90-112">Por exemplo, em vez de usar o campo <xref:System.IO.Path.InvalidPathChars>, você deve usar o método <xref:System.IO.Path.GetInvalidPathChars%2A>.</span><span class="sxs-lookup"><span data-stu-id="04f90-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="04f90-113">Observe que os tipos de .NET Framework não usam os campos públicos para definir tipos de limite internamente.</span><span class="sxs-lookup"><span data-stu-id="04f90-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="04f90-114">Em vez disso, o .NET Framework usa campos particulares separados.</span><span class="sxs-lookup"><span data-stu-id="04f90-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="04f90-115">A alteração dos valores desses campos públicos não altera o comportamento dos tipos de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04f90-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f90-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="04f90-116">See also</span></span>

- [<span data-ttu-id="04f90-117">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="04f90-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
