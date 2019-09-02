---
title: Código transparente de segurança, nível 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61a436efe3e3af7ce4aa50afe242838b1cd8941e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206073"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="85941-102">Código transparente de segurança, nível 2</span><span class="sxs-lookup"><span data-stu-id="85941-102">Security-Transparent Code, Level 2</span></span>

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="85941-103">A transparência de nível 2 foi introduzida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="85941-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="85941-104">As três filosofias desse modelo são código Transparent, segurança – código crítico e com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="85941-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="85941-105">O código Transparent, incluindo o código que está sendo executado como confiança total, pode chamar outros códigos transparentes ou somente com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="85941-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="85941-106">Ele só pode executar ações permitidas pelo conjunto de permissões de confiança parcial do domínio (se houver).</span><span class="sxs-lookup"><span data-stu-id="85941-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="85941-107">O código transparent não pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="85941-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="85941-108">Execute uma <xref:System.Security.CodeAccessPermission.Assert%2A> elevação de privilégio.</span><span class="sxs-lookup"><span data-stu-id="85941-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="85941-109">Conter código não seguro ou não verificável.</span><span class="sxs-lookup"><span data-stu-id="85941-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="85941-110">Chame diretamente o código crítico.</span><span class="sxs-lookup"><span data-stu-id="85941-110">Directly call critical code.</span></span>

  - <span data-ttu-id="85941-111">Chame código nativo ou código com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="85941-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="85941-112">Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="85941-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="85941-113">Herdar de tipos críticos.</span><span class="sxs-lookup"><span data-stu-id="85941-113">Inherit from critical types.</span></span>

  <span data-ttu-id="85941-114">Além disso, os métodos Transparent não podem substituir métodos virtuais críticos nem implementar métodos de interface críticos.</span><span class="sxs-lookup"><span data-stu-id="85941-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="85941-115">O código crítico seguro é totalmente confiável, mas é possível chamá-lo por código Transparent.</span><span class="sxs-lookup"><span data-stu-id="85941-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="85941-116">Ele expõe uma área de superfície limitada de código de confiança total; a correção e as verificações de segurança ocorrem em código crítico seguro.</span><span class="sxs-lookup"><span data-stu-id="85941-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="85941-117">O código de segurança crítica pode chamar qualquer código e é totalmente confiável, mas não pode ser chamado pelo código Transparent.</span><span class="sxs-lookup"><span data-stu-id="85941-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

<span data-ttu-id="85941-118">Esse tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="85941-118">This topic contains the following sections:</span></span>

- [<span data-ttu-id="85941-119">Exemplos de uso e comportamentos</span><span class="sxs-lookup"><span data-stu-id="85941-119">Usage Examples and Behaviors</span></span>](#examples)

- [<span data-ttu-id="85941-120">Padrões de substituição</span><span class="sxs-lookup"><span data-stu-id="85941-120">Override Patterns</span></span>](#override)

- [<span data-ttu-id="85941-121">Regras de herança</span><span class="sxs-lookup"><span data-stu-id="85941-121">Inheritance Rules</span></span>](#inheritance)

- [<span data-ttu-id="85941-122">Informações e regras adicionais</span><span class="sxs-lookup"><span data-stu-id="85941-122">Additional Information and Rules</span></span>](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="85941-123">Exemplos de Uso e Comportamentos</span><span class="sxs-lookup"><span data-stu-id="85941-123">Usage Examples and Behaviors</span></span>

<span data-ttu-id="85941-124">Para especificar .NET Framework regras de 4 (transparência de nível 2), use a seguinte anotação para um assembly:</span><span class="sxs-lookup"><span data-stu-id="85941-124">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="85941-125">Para bloquear as regras do .NET Framework 2,0 (transparência de nível 1), use a seguinte anotação:</span><span class="sxs-lookup"><span data-stu-id="85941-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="85941-126">Se você não anotar um assembly, as regras .NET Framework 4 serão usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="85941-126">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="85941-127">No entanto, a prática recomendada é usar o <xref:System.Security.SecurityRulesAttribute> atributo em vez de dependendo do padrão.</span><span class="sxs-lookup"><span data-stu-id="85941-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="85941-128">Anotação em todo o assembly</span><span class="sxs-lookup"><span data-stu-id="85941-128">Assembly-wide Annotation</span></span>

<span data-ttu-id="85941-129">As regras a seguir se aplicam ao uso de atributos no nível do assembly:</span><span class="sxs-lookup"><span data-stu-id="85941-129">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="85941-130">Nenhum atributo: Se você não especificar nenhum atributo, o tempo de execução interpretará todo o código como segurança crítica, exceto onde a segurança crítica viola uma regra de herança (por exemplo, ao substituir ou implementar um método de interface ou virtual transparente).</span><span class="sxs-lookup"><span data-stu-id="85941-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="85941-131">Nesses casos, os métodos são de segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="85941-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="85941-132">Especificar nenhum atributo faz com que o Common Language Runtime determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="85941-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="85941-133">`SecurityTransparent`: Todo o código é transparente; o assembly inteiro não fará nada privilegiado nem seguro.</span><span class="sxs-lookup"><span data-stu-id="85941-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="85941-134">`SecurityCritical`: Todo o código introduzido por tipos neste assembly é crítico; todo o outro código é transparente.</span><span class="sxs-lookup"><span data-stu-id="85941-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="85941-135">Esse cenário é semelhante a não especificar nenhum atributo; no entanto, o Common Language Runtime não determina automaticamente as regras de transparência.</span><span class="sxs-lookup"><span data-stu-id="85941-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="85941-136">Por exemplo, se você substituir um método virtual ou abstract ou implementar um método de interface, por padrão, esse método será transparente.</span><span class="sxs-lookup"><span data-stu-id="85941-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="85941-137">Você deve anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`; caso contrário, <xref:System.TypeLoadException> um será lançado em tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="85941-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="85941-138">Essa regra também se aplica quando a classe base e a classe derivada estão no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="85941-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="85941-139">`AllowPartiallyTrustedCallers`(somente nível 2): Todos os padrões de código são transparentes.</span><span class="sxs-lookup"><span data-stu-id="85941-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="85941-140">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="85941-140">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="85941-141">A tabela a seguir compara o comportamento de nível de assembly para o nível 2 com o nível 1.</span><span class="sxs-lookup"><span data-stu-id="85941-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="85941-142">Atributo de assembly</span><span class="sxs-lookup"><span data-stu-id="85941-142">Assembly attribute</span></span>|<span data-ttu-id="85941-143">Nível 2</span><span class="sxs-lookup"><span data-stu-id="85941-143">Level 2</span></span>|<span data-ttu-id="85941-144">Nível 1</span><span class="sxs-lookup"><span data-stu-id="85941-144">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="85941-145">Nenhum atributo em um assembly parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="85941-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="85941-146">Os tipos e membros são, por padrão, transparentes, mas podem ser críticos para segurança ou com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="85941-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="85941-147">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="85941-147">All types and members are transparent.</span></span>|
|<span data-ttu-id="85941-148">Nenhum atributo</span><span class="sxs-lookup"><span data-stu-id="85941-148">No attribute</span></span>|<span data-ttu-id="85941-149">Especificar nenhum atributo faz com que o Common Language Runtime determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="85941-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="85941-150">Todos os tipos e membros são críticos à segurança, exceto onde a segurança crítica viola uma regra de herança.</span><span class="sxs-lookup"><span data-stu-id="85941-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="85941-151">Em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`), todos os tipos são transparentes e todos os membros são críticos à segurança.</span><span class="sxs-lookup"><span data-stu-id="85941-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="85941-152">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="85941-152">All types and members are transparent.</span></span>|<span data-ttu-id="85941-153">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="85941-153">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="85941-154">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="85941-154">Not applicable.</span></span>|<span data-ttu-id="85941-155">Todos os tipos e membros são críticos para a segurança.</span><span class="sxs-lookup"><span data-stu-id="85941-155">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="85941-156">Todo o código introduzido por tipos neste assembly é crítico; todo o outro código é transparente.</span><span class="sxs-lookup"><span data-stu-id="85941-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="85941-157">Se você substituir um método virtual ou abstract ou implementar um método de interface, deverá anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="85941-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="85941-158">Todos os padrões de código são transparentes.</span><span class="sxs-lookup"><span data-stu-id="85941-158">All code defaults to transparent.</span></span> <span data-ttu-id="85941-159">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="85941-159">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="85941-160">Tipo e Anotação do Membro</span><span class="sxs-lookup"><span data-stu-id="85941-160">Type and Member Annotation</span></span>

<span data-ttu-id="85941-161">Os atributos de segurança que são aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="85941-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="85941-162">No entanto, eles não se aplicam a substituições virtuais ou abstratas da classe base ou implementações de interface.</span><span class="sxs-lookup"><span data-stu-id="85941-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="85941-163">As regras a seguir se aplicam ao uso de atributos no nível de tipo e de membro:</span><span class="sxs-lookup"><span data-stu-id="85941-163">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="85941-164">`SecurityCritical`: O tipo ou o membro é crítico e pode ser chamado somente pelo código de confiança total.</span><span class="sxs-lookup"><span data-stu-id="85941-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="85941-165">Os métodos que são introduzidos em um tipo de segurança crítica são críticos.</span><span class="sxs-lookup"><span data-stu-id="85941-165">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="85941-166">Os métodos virtuais e abstratos que são introduzidos em classes base ou interfaces, e substituídos ou implementados em uma classe de segurança crítica são transparentes por padrão.</span><span class="sxs-lookup"><span data-stu-id="85941-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="85941-167">Eles devem ser identificados como `SecuritySafeCritical` ou. `SecurityCritical`</span><span class="sxs-lookup"><span data-stu-id="85941-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="85941-168">`SecuritySafeCritical`: O tipo ou o membro é de segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="85941-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="85941-169">No entanto, o tipo ou membro pode ser chamado de código transparente (parcialmente confiável) e é compatível como qualquer outro código crítico.</span><span class="sxs-lookup"><span data-stu-id="85941-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="85941-170">O código deve ser auditado quanto à segurança.</span><span class="sxs-lookup"><span data-stu-id="85941-170">The code must be audited for security.</span></span>

[<span data-ttu-id="85941-171">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="85941-171">Back to top</span></span>](#top)

<a name="override"></a>

## <a name="override-patterns"></a><span data-ttu-id="85941-172">Substituir Padrões</span><span class="sxs-lookup"><span data-stu-id="85941-172">Override Patterns</span></span>

<span data-ttu-id="85941-173">A tabela a seguir mostra as substituições de método permitidas para transparência de nível 2.</span><span class="sxs-lookup"><span data-stu-id="85941-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="85941-174">Membro de interface/virtual base</span><span class="sxs-lookup"><span data-stu-id="85941-174">Base virtual/interface member</span></span>|<span data-ttu-id="85941-175">Substituição/interface</span><span class="sxs-lookup"><span data-stu-id="85941-175">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[<span data-ttu-id="85941-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="85941-176">Back to top</span></span>](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a><span data-ttu-id="85941-177">Regras de Herança</span><span class="sxs-lookup"><span data-stu-id="85941-177">Inheritance Rules</span></span>

<span data-ttu-id="85941-178">Nesta seção, a seguinte ordem é atribuída a `Transparent`, `Critical`e `SafeCritical` a código com base no acesso e nos recursos:</span><span class="sxs-lookup"><span data-stu-id="85941-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="85941-179">Regras para tipos: Indo da esquerda para a direita, o acesso se torna mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="85941-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="85941-180">Os tipos derivados devem ser pelo menos tão restritivos quanto o tipo base.</span><span class="sxs-lookup"><span data-stu-id="85941-180">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="85941-181">Regras para métodos: Os métodos derivados não podem alterar a acessibilidade do método base.</span><span class="sxs-lookup"><span data-stu-id="85941-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="85941-182">Para o comportamento padrão, todos os métodos derivados que não são anotados são `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="85941-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="85941-183">Derivações de tipos críticos causam uma exceção a ser gerada se o método substituído não for anotado explicitamente como `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="85941-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="85941-184">A tabela a seguir mostra os padrões de herança de tipo permitidos.</span><span class="sxs-lookup"><span data-stu-id="85941-184">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="85941-185">Classe base</span><span class="sxs-lookup"><span data-stu-id="85941-185">Base class</span></span>|<span data-ttu-id="85941-186">A classe derivada pode ser</span><span class="sxs-lookup"><span data-stu-id="85941-186">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="85941-187">A tabela a seguir mostra os padrões de herança de tipo não permitido.</span><span class="sxs-lookup"><span data-stu-id="85941-187">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="85941-188">Classe base</span><span class="sxs-lookup"><span data-stu-id="85941-188">Base class</span></span>|<span data-ttu-id="85941-189">A classe derivada não pode ser</span><span class="sxs-lookup"><span data-stu-id="85941-189">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="85941-190">A tabela a seguir mostra os padrões de herança de método permitidos.</span><span class="sxs-lookup"><span data-stu-id="85941-190">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="85941-191">Método base</span><span class="sxs-lookup"><span data-stu-id="85941-191">Base method</span></span>|<span data-ttu-id="85941-192">O método derivado pode ser</span><span class="sxs-lookup"><span data-stu-id="85941-192">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="85941-193">A tabela a seguir mostra os padrões de herança de método não permitido.</span><span class="sxs-lookup"><span data-stu-id="85941-193">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="85941-194">Método base</span><span class="sxs-lookup"><span data-stu-id="85941-194">Base method</span></span>|<span data-ttu-id="85941-195">O método derivado não pode ser</span><span class="sxs-lookup"><span data-stu-id="85941-195">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="85941-196">Essas regras de herança se aplicam a tipos e membros de nível 2.</span><span class="sxs-lookup"><span data-stu-id="85941-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="85941-197">Os tipos em assemblies de nível 1 podem herdar de membros e tipos de segurança de nível 2-críticos.</span><span class="sxs-lookup"><span data-stu-id="85941-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="85941-198">Portanto, os tipos de nível 2 e os membros devem ter demandas de herança separadas para herdeiros de nível 1.</span><span class="sxs-lookup"><span data-stu-id="85941-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

[<span data-ttu-id="85941-199">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="85941-199">Back to top</span></span>](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a><span data-ttu-id="85941-200">Informações Adicionais e Regras</span><span class="sxs-lookup"><span data-stu-id="85941-200">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="85941-201">Suporte LinkDemand</span><span class="sxs-lookup"><span data-stu-id="85941-201">LinkDemand Support</span></span>

<span data-ttu-id="85941-202">O modelo de transparência nível 2 substitui <xref:System.Security.Permissions.SecurityAction.LinkDemand> o <xref:System.Security.SecurityCriticalAttribute> pelo atributo.</span><span class="sxs-lookup"><span data-stu-id="85941-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="85941-203">No código herdado (nível 1), <xref:System.Security.Permissions.SecurityAction.LinkDemand> um é automaticamente tratado como <xref:System.Security.Permissions.SecurityAction.Demand>um.</span><span class="sxs-lookup"><span data-stu-id="85941-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="85941-204">Reflexão</span><span class="sxs-lookup"><span data-stu-id="85941-204">Reflection</span></span>

<span data-ttu-id="85941-205">Invocar um método crítico ou ler um campo crítico dispara uma demanda de confiança total (assim como se você estivesse invocando um método ou um campo particular).</span><span class="sxs-lookup"><span data-stu-id="85941-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="85941-206">Portanto, o código de confiança total pode invocar um método crítico, enquanto o código de confiança parcial não pode.</span><span class="sxs-lookup"><span data-stu-id="85941-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="85941-207">As propriedades a seguir foram adicionadas ao <xref:System.Reflection> namespace para determinar se o tipo, o método ou o campo `SecurityCritical`é `SecuritySafeCritical`,, `SecurityTransparent`ou <xref:System.Type.IsSecurityCritical%2A>: <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="85941-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="85941-208">Use essas propriedades para determinar a transparência usando reflexão em vez de verificar a presença do atributo.</span><span class="sxs-lookup"><span data-stu-id="85941-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="85941-209">As regras de transparência são complexas e a verificação do atributo pode não ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="85941-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="85941-210">Um `SafeCritical` método retorna `true` para <xref:System.Type.IsSecurityCritical%2A> and ,<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> porque`SafeCritical` é realmente crítico (ele tem os mesmos recursos que o código crítico, mas pode ser chamado a partir do código Transparent).</span><span class="sxs-lookup"><span data-stu-id="85941-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="85941-211">Métodos dinâmicos herdam a transparência dos módulos aos quais eles estão anexados; Eles não herdam a transparência do tipo (se estiverem anexados a um tipo).</span><span class="sxs-lookup"><span data-stu-id="85941-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="85941-212">Ignorar Verificação em Confiança Total</span><span class="sxs-lookup"><span data-stu-id="85941-212">Skip Verification in Full Trust</span></span>

<span data-ttu-id="85941-213">Você pode ignorar a verificação de assemblies transparentes totalmente confiáveis <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> definindo a `true` Propriedade como <xref:System.Security.SecurityRulesAttribute> no atributo:</span><span class="sxs-lookup"><span data-stu-id="85941-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="85941-214">A <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade é `false` por padrão, portanto, a propriedade deve ser definida `true` como para ignorar a verificação.</span><span class="sxs-lookup"><span data-stu-id="85941-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="85941-215">Isso deve ser feito apenas para fins de otimização.</span><span class="sxs-lookup"><span data-stu-id="85941-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="85941-216">Você deve garantir que o código transparent no assembly seja verificável usando a `transparent` opção na [ferramenta PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="85941-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85941-217">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85941-217">See also</span></span>

- [<span data-ttu-id="85941-218">Segurança-código Transparent, nível 1</span><span class="sxs-lookup"><span data-stu-id="85941-218">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="85941-219">Alterações de segurança</span><span class="sxs-lookup"><span data-stu-id="85941-219">Security Changes</span></span>](../security/security-changes.md)
