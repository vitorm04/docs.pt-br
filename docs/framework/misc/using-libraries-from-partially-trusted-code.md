---
title: "Usando bibliotecas de código parcialmente confiável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a452370df7c18f3e3f0190a14979099152485f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a><span data-ttu-id="431db-102">Usando bibliotecas de código parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="431db-102">Using Libraries from Partially Trusted Code</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  <span data-ttu-id="431db-103">Este tópico aborda o comportamento de assemblies de nomes fortes e aplica-se somente a [nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies.</span><span class="sxs-lookup"><span data-stu-id="431db-103">This topic addresses the behavior of strong-named assemblies and applies only to [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies.</span></span> <span data-ttu-id="431db-104">[Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou posterior, não são afetados por nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="431db-104">[Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later are not affected by strong names.</span></span> <span data-ttu-id="431db-105">Para obter mais informações sobre as alterações no sistema de segurança, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="431db-105">For more information about changes to the security system, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="431db-106">Aplicativos que recebem menos do que a confiança total do seu host ou de área restrita não tem permissão para chamar compartilhado bibliotecas gerenciadas, a menos que o gravador da biblioteca permita, especificamente, através do uso do <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="431db-106">Applications that receive less than full trust from their host or sandbox are not allowed to call shared managed libraries unless the library writer specifically allows them to through the use of the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="431db-107">Portanto, autores de aplicativos devem estar cientes de que algumas bibliotecas não estarão disponíveis para eles em um contexto parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="431db-107">Therefore, application writers must be aware that some libraries will not be available to them from a partially trusted context.</span></span> <span data-ttu-id="431db-108">Por padrão, todo o código que que executa em uma confiança parcial [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) e não é a lista de assemblies de confiança total é parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="431db-108">By default, all code that executes in a partial-trust [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) and is not in the list of full-trust assemblies is partially trusted.</span></span> <span data-ttu-id="431db-109">Se você não espera que seu código deve ser executado em um contexto parcialmente confiável ou ser chamado por código parcialmente confiável, você não precisa se preocupar com as informações nesta seção.</span><span class="sxs-lookup"><span data-stu-id="431db-109">If you do not expect your code to be executed from a partially trusted context or to be called by partially trusted code, you do not have to be concerned about the information in this section.</span></span> <span data-ttu-id="431db-110">No entanto, se você escrever código que deve interagir com código parcialmente confiável ou não funcione em um contexto parcialmente confiável, você deve considerar os seguintes fatores:</span><span class="sxs-lookup"><span data-stu-id="431db-110">However, if you write code that must interact with partially trusted code or operate from a partially trusted context, you should consider the following factors:</span></span>  
  
-   <span data-ttu-id="431db-111">Bibliotecas devem ser assinadas com um nome forte para ser compartilhado por vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="431db-111">Libraries must be signed with a strong name in order to be shared by multiple applications.</span></span> <span data-ttu-id="431db-112">Nomes fortes permitir que seu código seja colocado no cache de assembly global ou adicionado à lista de confiança total de um modo seguro <xref:System.AppDomain>, e permitem que os consumidores verificar se uma determinada parte do código móvel realmente provém de você.</span><span class="sxs-lookup"><span data-stu-id="431db-112">Strong names allow your code to be placed in the global assembly cache or added to the full-trust list of a sandboxing <xref:System.AppDomain>, and allow consumers to verify that a particular piece of mobile code actually originates from you.</span></span>  
  
-   <span data-ttu-id="431db-113">Por padrão, nomes fortes [nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md) bibliotecas compartilhadas executam implícita [LinkDemand](../../../docs/framework/misc/link-demands.md) completa confiar automaticamente, sem o gravador da biblioteca precisar fazer algo.</span><span class="sxs-lookup"><span data-stu-id="431db-113">By default, strong-named [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) shared libraries perform an implicit [LinkDemand](../../../docs/framework/misc/link-demands.md) for full trust automatically, without the library writer having to do anything.</span></span>  
  
-   <span data-ttu-id="431db-114">Se um chamador não tem a confiança total, mas ainda tenta chamar uma biblioteca, o tempo de execução lança um <xref:System.Security.SecurityException> e o chamador não tem permissão para vincular à biblioteca.</span><span class="sxs-lookup"><span data-stu-id="431db-114">If a caller does not have full trust but still tries to call such a library, the runtime throws a <xref:System.Security.SecurityException> and the caller is not allowed to link to the library.</span></span>  
  
-   <span data-ttu-id="431db-115">Para desabilitar o automático **LinkDemand** e evitar a exceção de que está sendo lançada, você pode colocar o **AllowPartiallyTrustedCallersAttribute** atributo no escopo do assembly de compartilhado biblioteca.</span><span class="sxs-lookup"><span data-stu-id="431db-115">In order to disable the automatic **LinkDemand** and prevent the exception from being thrown, you can place the **AllowPartiallyTrustedCallersAttribute** attribute on the assembly scope of a shared library.</span></span> <span data-ttu-id="431db-116">Este atributo permite suas bibliotecas ser chamado do código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="431db-116">This attribute allows your libraries to be called from partially trusted managed code.</span></span>  
  
-   <span data-ttu-id="431db-117">Código parcialmente confiável que é concedido acesso a uma biblioteca com esse atributo é ainda sujeita a mais restrições definidas pelo <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="431db-117">Partially trusted code that is granted access to a library with this attribute is still subject to further restrictions defined by the <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="431db-118">Não é possível através de programação para código parcialmente confiável chame uma biblioteca que não tem o **AllowPartiallyTrustedCallersAttribute** atributo.</span><span class="sxs-lookup"><span data-stu-id="431db-118">There is no programmatic way for partially trusted code to call a library that does not have the **AllowPartiallyTrustedCallersAttribute** attribute.</span></span>  
  
 <span data-ttu-id="431db-119">Bibliotecas que são particulares a um aplicativo específico não exigem um nome forte ou **AllowPartiallyTrustedCallersAttribute** de atributos e não pode ser referenciado por códigos possivelmente mal-intencionados fora do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="431db-119">Libraries that are private to a specific application do not require a strong name or the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be referenced by potentially malicious code outside the application.</span></span> <span data-ttu-id="431db-120">Esse código está protegido contra uso indevido intencional ou não pelo código parcialmente confiável de móvel sem que o desenvolvedor precisar fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="431db-120">Such code is protected against intentional or unintentional misuse by partially trusted mobile code without the developer having to do anything extra.</span></span>  
  
 <span data-ttu-id="431db-121">Considere a possibilidade de habilitar explicitamente o uso por código parcialmente confiável para os seguintes tipos de código:</span><span class="sxs-lookup"><span data-stu-id="431db-121">You should consider explicitly enabling use by partially trusted code for the following types of code:</span></span>  
  
-   <span data-ttu-id="431db-122">Código que foi testado cuidadosamente quanto a vulnerabilidades de segurança e está em conformidade com as diretrizes descritas em [diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="431db-122">Code that has been diligently tested for security vulnerabilities and is in compliance with the guidelines described in [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md).</span></span>  
  
-   <span data-ttu-id="431db-123">Bibliotecas de código fortes que são escritas especificamente para cenários parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="431db-123">Strong-named code libraries that are specifically written for partially trusted scenarios.</span></span>  
  
-   <span data-ttu-id="431db-124">Todos os componentes (se parcialmente ou totalmente confiável) assinado com um nome forte que será chamado pelo código que é baixado da Internet.</span><span class="sxs-lookup"><span data-stu-id="431db-124">Any components (whether partially or fully trusted) signed with a strong name that will be called by code that is downloaded from the Internet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="431db-125">Algumas classes na biblioteca de classes do .NET Framework não tem o **AllowPartiallyTrustedCallersAttribute** de atributos e não pode ser chamado por código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="431db-125">Some classes in the .NET Framework class library do not have the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be called by partially trusted code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431db-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="431db-126">See Also</span></span>  
 [<span data-ttu-id="431db-127">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="431db-127">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
