---
title: "Código transparente de segurança, nível 2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0bd4ee6c43b5089c45789b4f22326e17ec2218c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="bb609-102">Código transparente de segurança, nível 2</span><span class="sxs-lookup"><span data-stu-id="bb609-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="bb609-103">Transparência de nível 2 foi introduzida no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb609-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="bb609-104">Os três princípios desse modelo são código transparente, código de segurança crítica segura e código crítico de segurança.</span><span class="sxs-lookup"><span data-stu-id="bb609-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="bb609-105">Código transparente, incluindo o código que está executando em confiança total, pode chamar outro código transparente ou somente código de segurança crítica segura.</span><span class="sxs-lookup"><span data-stu-id="bb609-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="bb609-106">Ele só pode executar ações permitidas pela permissão de confiança parcial do domínio definido (se houver).</span><span class="sxs-lookup"><span data-stu-id="bb609-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="bb609-107">Código transparente não pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="bb609-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="bb609-108">Executar um <xref:System.Security.CodeAccessPermission.Assert%2A> ou elevação de privilégio.</span><span class="sxs-lookup"><span data-stu-id="bb609-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="bb609-109">Contém o código não confiável ou.</span><span class="sxs-lookup"><span data-stu-id="bb609-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="bb609-110">Chame diretamente o código crítico.</span><span class="sxs-lookup"><span data-stu-id="bb609-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="bb609-111">Chamar código nativo ou com o código de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="bb609-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="bb609-112">Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="bb609-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="bb609-113">Herda de tipos críticos.</span><span class="sxs-lookup"><span data-stu-id="bb609-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="bb609-114">Além disso, os métodos transparentes não é possível substituir métodos virtuais críticos ou implementar métodos de interface crítico.</span><span class="sxs-lookup"><span data-stu-id="bb609-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="bb609-115">Código crítico de segurança é totalmente confiável, mas pode ser chamado por código transparente.</span><span class="sxs-lookup"><span data-stu-id="bb609-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="bb609-116">Ela expõe uma área da superfície limitada do código de confiança total; verificações de integridade e segurança acontecem no código crítico para segurança.</span><span class="sxs-lookup"><span data-stu-id="bb609-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="bb609-117">Código crítico de segurança pode chamar qualquer código e é totalmente confiável, mas ele não pode ser chamado por código transparente.</span><span class="sxs-lookup"><span data-stu-id="bb609-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="bb609-118">Esse tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="bb609-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="bb609-119">Comportamentos e exemplos de uso</span><span class="sxs-lookup"><span data-stu-id="bb609-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="bb609-120">Padrões de substituição</span><span class="sxs-lookup"><span data-stu-id="bb609-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="bb609-121">Regras de herança</span><span class="sxs-lookup"><span data-stu-id="bb609-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="bb609-122">Regras e informações adicionais</span><span class="sxs-lookup"><span data-stu-id="bb609-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="bb609-123">Exemplos de Uso e Comportamentos</span><span class="sxs-lookup"><span data-stu-id="bb609-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="bb609-124">Para especificar [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras (transparência de nível 2), use a anotação a seguir para um assembly:</span><span class="sxs-lookup"><span data-stu-id="bb609-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="bb609-125">Para bloquear nas regras do .NET Framework 2.0 (transparência de nível 1), use a anotação a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb609-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="bb609-126">Se você não anotar um assembly, o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras são usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="bb609-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="bb609-127">No entanto, a prática recomendada é usar o <xref:System.Security.SecurityRulesAttribute> de atributo, em vez de dependendo do padrão.</span><span class="sxs-lookup"><span data-stu-id="bb609-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="bb609-128">Anotação de todo o assembly</span><span class="sxs-lookup"><span data-stu-id="bb609-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="bb609-129">As seguintes regras se aplicam ao uso de atributos em nível de assembly:</span><span class="sxs-lookup"><span data-stu-id="bb609-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="bb609-130">Nenhum atributo: se você não especificar os atributos, o tempo de execução interpreta todo o código como críticas de segurança, exceto onde sendo críticas de segurança viola uma regra de herança (por exemplo, ao substituir ou implementar um transparente virtual ou o método de interface ).</span><span class="sxs-lookup"><span data-stu-id="bb609-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="bb609-131">Nesses casos, os métodos são crítico para segurança.</span><span class="sxs-lookup"><span data-stu-id="bb609-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="bb609-132">Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="bb609-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   <span data-ttu-id="bb609-133">`SecurityTransparent`: Todo o código é transparente; o conjunto inteiro não fará nada privilegiada ou não seguro.</span><span class="sxs-lookup"><span data-stu-id="bb609-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   <span data-ttu-id="bb609-134">`SecurityCritical`: Todo o código que é apresentado pelo tipos neste assembly é importante; todos os outros códigos é transparente.</span><span class="sxs-lookup"><span data-stu-id="bb609-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="bb609-135">Este cenário é semelhante à especificação não todos os atributos; No entanto, o common language runtime não determinar automaticamente as regras de transparência.</span><span class="sxs-lookup"><span data-stu-id="bb609-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="bb609-136">Por exemplo, se você substituir um método virtual ou abstrato ou implementa um método de interface, por padrão, esse método é transparente.</span><span class="sxs-lookup"><span data-stu-id="bb609-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="bb609-137">Você deve explicitamente anotar o método como `SecurityCritical` ou `SecuritySafeCritical`; caso contrário, um <xref:System.TypeLoadException> será lançada em tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="bb609-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="bb609-138">Esta regra também se aplica quando a classe base e a classe derivada no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="bb609-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   <span data-ttu-id="bb609-139">`AllowPartiallyTrustedCallers`(nível 2 somente): todos os padrões para transparente de código.</span><span class="sxs-lookup"><span data-stu-id="bb609-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="bb609-140">No entanto, membros e tipos individuais podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="bb609-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="bb609-141">A tabela a seguir compara o comportamento de nível de assembly para o nível 2 com o nível 1.</span><span class="sxs-lookup"><span data-stu-id="bb609-141">The following table compares the assembly level behavior for Level 2 with Level 1 .</span></span>  
  
|<span data-ttu-id="bb609-142">Atributo de assembly</span><span class="sxs-lookup"><span data-stu-id="bb609-142">Assembly attribute</span></span>|<span data-ttu-id="bb609-143">Nível 2</span><span class="sxs-lookup"><span data-stu-id="bb609-143">Level 2</span></span>|<span data-ttu-id="bb609-144">Nível 1</span><span class="sxs-lookup"><span data-stu-id="bb609-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="bb609-145">Nenhum atributo em um assembly parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="bb609-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="bb609-146">Tipos e membros são por padrão transparente, mas podem ser crítico de segurança ou segurança crítica safe.</span><span class="sxs-lookup"><span data-stu-id="bb609-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="bb609-147">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="bb609-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="bb609-148">Nenhum atributo</span><span class="sxs-lookup"><span data-stu-id="bb609-148">No attribute</span></span>|<span data-ttu-id="bb609-149">Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="bb609-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="bb609-150">Todos os tipos e membros são críticas de segurança, exceto onde sendo críticas de segurança viola uma regra de herança.</span><span class="sxs-lookup"><span data-stu-id="bb609-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="bb609-151">Em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`) todos os tipos são transparentes e todos os membros são safe-crítico de segurança.</span><span class="sxs-lookup"><span data-stu-id="bb609-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="bb609-152">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="bb609-152">All types and members are transparent.</span></span>|<span data-ttu-id="bb609-153">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="bb609-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="bb609-154">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="bb609-154">Not applicable.</span></span>|<span data-ttu-id="bb609-155">Todos os tipos e membros são críticas de segurança.</span><span class="sxs-lookup"><span data-stu-id="bb609-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="bb609-156">Todo o código que é apresentado pelo tipos neste assembly é importante; todos os outros códigos é transparente.</span><span class="sxs-lookup"><span data-stu-id="bb609-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="bb609-157">Se você substituir um método virtual ou abstrato ou implementa um método de interface, você deve explicitamente anotar o método como `SecurityCritical` ou `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="bb609-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="bb609-158">Todos os padrões para transparente de código.</span><span class="sxs-lookup"><span data-stu-id="bb609-158">All code defaults to transparent.</span></span> <span data-ttu-id="bb609-159">No entanto, membros e tipos individuais podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="bb609-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="bb609-160">Tipo e Anotação do Membro</span><span class="sxs-lookup"><span data-stu-id="bb609-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="bb609-161">Os atributos de segurança que são aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="bb609-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="bb609-162">No entanto, eles não se aplicam ao virtual ou abstrato substitui as implementações de interface ou classe base.</span><span class="sxs-lookup"><span data-stu-id="bb609-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="bb609-163">As seguintes regras se aplicam ao uso de atributos em nível de tipo e membro:</span><span class="sxs-lookup"><span data-stu-id="bb609-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   <span data-ttu-id="bb609-164">`SecurityCritical`: O tipo ou membro é fundamental e pode ser chamado apenas pelo código de confiança total.</span><span class="sxs-lookup"><span data-stu-id="bb609-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="bb609-165">Os métodos que foram introduzidos em um tipo crítico de segurança são essenciais.</span><span class="sxs-lookup"><span data-stu-id="bb609-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bb609-166">Métodos abstratos e virtuais que são introduzidos no interfaces ou classes base e substituídos ou implementados em uma classe críticas de segurança são transparentes por padrão.</span><span class="sxs-lookup"><span data-stu-id="bb609-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="bb609-167">Eles devem ser identificados como `SecuritySafeCritical` ou `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="bb609-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   <span data-ttu-id="bb609-168">`SecuritySafeCritical`: O tipo ou membro é crítico para segurança.</span><span class="sxs-lookup"><span data-stu-id="bb609-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="bb609-169">No entanto, o tipo ou membro pode ser chamado de código (parcialmente confiável) transparente e é capaz como qualquer outro código crítico.</span><span class="sxs-lookup"><span data-stu-id="bb609-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="bb609-170">O código deve ser auditado para segurança.</span><span class="sxs-lookup"><span data-stu-id="bb609-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="bb609-171">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="bb609-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="bb609-172">Substituir Padrões</span><span class="sxs-lookup"><span data-stu-id="bb609-172">Override Patterns</span></span>  
 <span data-ttu-id="bb609-173">A tabela a seguir mostra as substituições de método permitidas para a transparência de nível 2.</span><span class="sxs-lookup"><span data-stu-id="bb609-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="bb609-174">Membro de base virtual/de interface</span><span class="sxs-lookup"><span data-stu-id="bb609-174">Base virtual/interface member</span></span>|<span data-ttu-id="bb609-175">Substituição/de interface</span><span class="sxs-lookup"><span data-stu-id="bb609-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="bb609-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="bb609-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="bb609-177">Regras de Herança</span><span class="sxs-lookup"><span data-stu-id="bb609-177">Inheritance Rules</span></span>  
 <span data-ttu-id="bb609-178">Nesta seção, a ordem a seguir é atribuída a `Transparent`, `Critical`, e `SafeCritical` código com base no acesso e recursos:</span><span class="sxs-lookup"><span data-stu-id="bb609-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="bb609-179">Regras para tipos: vai da esquerda para a direita, acesso se torna mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="bb609-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="bb609-180">Tipos derivados devem ser pelo menos tão restritivos quanto o tipo base.</span><span class="sxs-lookup"><span data-stu-id="bb609-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="bb609-181">Regras para métodos: métodos derivados não é possível alterar a acessibilidade do método base.</span><span class="sxs-lookup"><span data-stu-id="bb609-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="bb609-182">Para o comportamento padrão, todos os métodos derivados que são anotados não são `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="bb609-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="bb609-183">Derivados dos tipos críticos causam uma exceção seja lançada se o método substituído não é anotado explicitamente como `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="bb609-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="bb609-184">A tabela a seguir mostra o tipo permitido padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="bb609-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="bb609-185">Classe base</span><span class="sxs-lookup"><span data-stu-id="bb609-185">Base class</span></span>|<span data-ttu-id="bb609-186">Classe derivada pode ser</span><span class="sxs-lookup"><span data-stu-id="bb609-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="bb609-187">A tabela a seguir mostra o tipo não permitido padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="bb609-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="bb609-188">Classe base</span><span class="sxs-lookup"><span data-stu-id="bb609-188">Base class</span></span>|<span data-ttu-id="bb609-189">Classe derivada não pode ser</span><span class="sxs-lookup"><span data-stu-id="bb609-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="bb609-190">A tabela a seguir mostra o método permitido padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="bb609-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="bb609-191">Método base</span><span class="sxs-lookup"><span data-stu-id="bb609-191">Base method</span></span>|<span data-ttu-id="bb609-192">Método derivado pode ser</span><span class="sxs-lookup"><span data-stu-id="bb609-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="bb609-193">A tabela a seguir mostra o método não permitido padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="bb609-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="bb609-194">Método base</span><span class="sxs-lookup"><span data-stu-id="bb609-194">Base method</span></span>|<span data-ttu-id="bb609-195">Método derivado não pode ser</span><span class="sxs-lookup"><span data-stu-id="bb609-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="bb609-196">Essas regras de herança se aplicam a membros e tipos de nível 2.</span><span class="sxs-lookup"><span data-stu-id="bb609-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="bb609-197">Tipos em assemblies de nível 1 podem herdar de membros e tipos de segurança crítica de nível 2.</span><span class="sxs-lookup"><span data-stu-id="bb609-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="bb609-198">Portanto, os membros e tipos de nível 2 devem ter demandas de herança separados para os herdeiros de nível 1.</span><span class="sxs-lookup"><span data-stu-id="bb609-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="bb609-199">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="bb609-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="bb609-200">Informações Adicionais e Regras</span><span class="sxs-lookup"><span data-stu-id="bb609-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="bb609-201">Suporte LinkDemand</span><span class="sxs-lookup"><span data-stu-id="bb609-201">LinkDemand Support</span></span>  
 <span data-ttu-id="bb609-202">O modelo de transparência de nível 2 substitui o <xref:System.Security.Permissions.SecurityAction.LinkDemand> com o <xref:System.Security.SecurityCriticalAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="bb609-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="bb609-203">No código herdado (nível 1), um <xref:System.Security.Permissions.SecurityAction.LinkDemand> automaticamente é tratado como um <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="bb609-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="bb609-204">Reflexão</span><span class="sxs-lookup"><span data-stu-id="bb609-204">Reflection</span></span>  
 <span data-ttu-id="bb609-205">Invocando um método crítico ou a leitura de um campo crítico dispara uma solicitação de confiança total (como se você invocou um campo ou método particular).</span><span class="sxs-lookup"><span data-stu-id="bb609-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="bb609-206">Portanto, o código de confiança total pode invocar um método crítico, enquanto que o código parcialmente confiável não pode.</span><span class="sxs-lookup"><span data-stu-id="bb609-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="bb609-207">As propriedades a seguir foram adicionadas para o <xref:System.Reflection> namespace para determinar se o tipo, método ou campo é `SecurityCritical`, `SecuritySafeCritical`, ou `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb609-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="bb609-208">Use essas propriedades para determinar a transparência por meio de reflexão em vez de verificar a presença do atributo.</span><span class="sxs-lookup"><span data-stu-id="bb609-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="bb609-209">As regras de transparência são complexas e verificando o atributo pode não ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="bb609-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb609-210">Um `SafeCritical` método retorna `true` para ambos <xref:System.Type.IsSecurityCritical%2A> e <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, pois `SafeCritical` é realmente importante (ele tem as mesmas capacidades de código crítico, mas ele pode ser chamado de código de transparência).</span><span class="sxs-lookup"><span data-stu-id="bb609-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="bb609-211">Métodos dinâmicos herdam a transparência de módulos que estão conectados a; eles não herdam a transparência do tipo (se eles estão conectados a um tipo).</span><span class="sxs-lookup"><span data-stu-id="bb609-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="bb609-212">Ignorar Verificação em Confiança Total</span><span class="sxs-lookup"><span data-stu-id="bb609-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="bb609-213">Você pode ignorar a verificação para totalmente confiáveis assemblies transparentes, definindo o <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade `true` no <xref:System.Security.SecurityRulesAttribute> atributo:</span><span class="sxs-lookup"><span data-stu-id="bb609-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="bb609-214">O <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> é de propriedade `false` por padrão, então a propriedade deve ser definida como `true` para ignorar a verificação.</span><span class="sxs-lookup"><span data-stu-id="bb609-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="bb609-215">Isso deve ser feito apenas a fins de otimização.</span><span class="sxs-lookup"><span data-stu-id="bb609-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="bb609-216">Você deve garantir que o código de transparência no assembly é verificado usando o `transparent` opção o [ferramenta PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="bb609-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb609-217">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb609-217">See Also</span></span>  
 [<span data-ttu-id="bb609-218">Código transparente de segurança, nível 1</span><span class="sxs-lookup"><span data-stu-id="bb609-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [<span data-ttu-id="bb609-219">Alterações de segurança</span><span class="sxs-lookup"><span data-stu-id="bb609-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
