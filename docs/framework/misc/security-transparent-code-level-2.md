---
title: Código transparente de segurança, nível 2
description: Entenda o código transparente de nível 2. Consulte exemplos de uso e comportamentos, padrões de substituição, regras de herança e muito mais.
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 3b87a48ac3f9925fd868be9e58d5904014ca6c09
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309203"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="db576-104">Código transparente de segurança, nível 2</span><span class="sxs-lookup"><span data-stu-id="db576-104">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="db576-105">A transparência de nível 2 foi introduzida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="db576-105">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="db576-106">As três filosofias desse modelo são código Transparent, segurança – código crítico e com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="db576-106">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="db576-107">O código Transparent, incluindo o código que está sendo executado como confiança total, pode chamar outros códigos transparentes ou somente com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="db576-107">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="db576-108">Ele só pode executar ações permitidas pelo conjunto de permissões de confiança parcial do domínio (se houver).</span><span class="sxs-lookup"><span data-stu-id="db576-108">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="db576-109">O código transparent não pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="db576-109">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="db576-110">Execute uma <xref:System.Security.CodeAccessPermission.Assert%2A> elevação de privilégio.</span><span class="sxs-lookup"><span data-stu-id="db576-110">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="db576-111">Conter código não seguro ou não verificável.</span><span class="sxs-lookup"><span data-stu-id="db576-111">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="db576-112">Chame diretamente o código crítico.</span><span class="sxs-lookup"><span data-stu-id="db576-112">Directly call critical code.</span></span>

  - <span data-ttu-id="db576-113">Chame código nativo ou código com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="db576-113">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="db576-114">Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand> .</span><span class="sxs-lookup"><span data-stu-id="db576-114">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="db576-115">Herdar de tipos críticos.</span><span class="sxs-lookup"><span data-stu-id="db576-115">Inherit from critical types.</span></span>

  <span data-ttu-id="db576-116">Além disso, os métodos Transparent não podem substituir métodos virtuais críticos nem implementar métodos de interface críticos.</span><span class="sxs-lookup"><span data-stu-id="db576-116">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="db576-117">O código crítico seguro é totalmente confiável, mas é possível chamá-lo por código Transparent.</span><span class="sxs-lookup"><span data-stu-id="db576-117">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="db576-118">Ele expõe uma área de superfície limitada de código de confiança total; a correção e as verificações de segurança ocorrem em código crítico seguro.</span><span class="sxs-lookup"><span data-stu-id="db576-118">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="db576-119">O código de segurança crítica pode chamar qualquer código e é totalmente confiável, mas não pode ser chamado pelo código Transparent.</span><span class="sxs-lookup"><span data-stu-id="db576-119">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="db576-120">Exemplos de Uso e Comportamentos</span><span class="sxs-lookup"><span data-stu-id="db576-120">Usage Examples and Behaviors</span></span>

<span data-ttu-id="db576-121">Para especificar .NET Framework regras de 4 (transparência de nível 2), use a seguinte anotação para um assembly:</span><span class="sxs-lookup"><span data-stu-id="db576-121">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="db576-122">Para bloquear as regras do .NET Framework 2,0 (transparência de nível 1), use a seguinte anotação:</span><span class="sxs-lookup"><span data-stu-id="db576-122">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="db576-123">Se você não anotar um assembly, as regras .NET Framework 4 serão usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="db576-123">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="db576-124">No entanto, a prática recomendada é usar o <xref:System.Security.SecurityRulesAttribute> atributo em vez de dependendo do padrão.</span><span class="sxs-lookup"><span data-stu-id="db576-124">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="db576-125">Anotação em todo o assembly</span><span class="sxs-lookup"><span data-stu-id="db576-125">Assembly-wide Annotation</span></span>

<span data-ttu-id="db576-126">As regras a seguir se aplicam ao uso de atributos no nível do assembly:</span><span class="sxs-lookup"><span data-stu-id="db576-126">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="db576-127">Nenhum atributo: se você não especificar nenhum atributo, o tempo de execução interpretará todo o código como segurança crítica, exceto onde a segurança crítica viola uma regra de herança (por exemplo, ao substituir ou implementar um método de interface ou virtual transparente).</span><span class="sxs-lookup"><span data-stu-id="db576-127">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="db576-128">Nesses casos, os métodos são de segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="db576-128">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="db576-129">Especificar nenhum atributo faz com que o Common Language Runtime determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="db576-129">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="db576-130">`SecurityTransparent`: Todo o código é transparente; o assembly inteiro não fará nada privilegiado nem seguro.</span><span class="sxs-lookup"><span data-stu-id="db576-130">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="db576-131">`SecurityCritical`: Todo o código introduzido por tipos neste assembly é crítico; todo o outro código é transparente.</span><span class="sxs-lookup"><span data-stu-id="db576-131">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="db576-132">Esse cenário é semelhante a não especificar nenhum atributo; no entanto, o Common Language Runtime não determina automaticamente as regras de transparência.</span><span class="sxs-lookup"><span data-stu-id="db576-132">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="db576-133">Por exemplo, se você substituir um método virtual ou abstract ou implementar um método de interface, por padrão, esse método será transparente.</span><span class="sxs-lookup"><span data-stu-id="db576-133">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="db576-134">Você deve anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical` ; caso contrário, um <xref:System.TypeLoadException> será lançado em tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="db576-134">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="db576-135">Essa regra também se aplica quando a classe base e a classe derivada estão no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="db576-135">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="db576-136">`AllowPartiallyTrustedCallers`(somente nível 2): todos os padrões de código são transparentes.</span><span class="sxs-lookup"><span data-stu-id="db576-136">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="db576-137">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="db576-137">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="db576-138">A tabela a seguir compara o comportamento de nível de assembly para o nível 2 com o nível 1.</span><span class="sxs-lookup"><span data-stu-id="db576-138">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="db576-139">Atributo de assembly</span><span class="sxs-lookup"><span data-stu-id="db576-139">Assembly attribute</span></span>|<span data-ttu-id="db576-140">Nível 2</span><span class="sxs-lookup"><span data-stu-id="db576-140">Level 2</span></span>|<span data-ttu-id="db576-141">Nível 1</span><span class="sxs-lookup"><span data-stu-id="db576-141">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="db576-142">Nenhum atributo em um assembly parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="db576-142">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="db576-143">Os tipos e membros são, por padrão, transparentes, mas podem ser críticos para segurança ou com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="db576-143">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="db576-144">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="db576-144">All types and members are transparent.</span></span>|
|<span data-ttu-id="db576-145">Nenhum atributo</span><span class="sxs-lookup"><span data-stu-id="db576-145">No attribute</span></span>|<span data-ttu-id="db576-146">Especificar nenhum atributo faz com que o Common Language Runtime determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="db576-146">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="db576-147">Todos os tipos e membros são críticos à segurança, exceto onde a segurança crítica viola uma regra de herança.</span><span class="sxs-lookup"><span data-stu-id="db576-147">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="db576-148">Em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain` ), todos os tipos são transparentes e todos os membros são críticos à segurança.</span><span class="sxs-lookup"><span data-stu-id="db576-148">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="db576-149">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="db576-149">All types and members are transparent.</span></span>|<span data-ttu-id="db576-150">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="db576-150">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="db576-151">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="db576-151">Not applicable.</span></span>|<span data-ttu-id="db576-152">Todos os tipos e membros são críticos para a segurança.</span><span class="sxs-lookup"><span data-stu-id="db576-152">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="db576-153">Todo o código introduzido por tipos neste assembly é crítico; todo o outro código é transparente.</span><span class="sxs-lookup"><span data-stu-id="db576-153">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="db576-154">Se você substituir um método virtual ou abstract ou implementar um método de interface, deverá anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical` .</span><span class="sxs-lookup"><span data-stu-id="db576-154">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="db576-155">Todos os padrões de código são transparentes.</span><span class="sxs-lookup"><span data-stu-id="db576-155">All code defaults to transparent.</span></span> <span data-ttu-id="db576-156">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="db576-156">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="db576-157">Tipo e Anotação do Membro</span><span class="sxs-lookup"><span data-stu-id="db576-157">Type and Member Annotation</span></span>

<span data-ttu-id="db576-158">Os atributos de segurança que são aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="db576-158">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="db576-159">No entanto, eles não se aplicam a substituições virtuais ou abstratas da classe base ou implementações de interface.</span><span class="sxs-lookup"><span data-stu-id="db576-159">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="db576-160">As regras a seguir se aplicam ao uso de atributos no nível de tipo e de membro:</span><span class="sxs-lookup"><span data-stu-id="db576-160">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="db576-161">`SecurityCritical`: O tipo ou membro é crítico e pode ser chamado somente pelo código de confiança total.</span><span class="sxs-lookup"><span data-stu-id="db576-161">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="db576-162">Os métodos que são introduzidos em um tipo de segurança crítica são críticos.</span><span class="sxs-lookup"><span data-stu-id="db576-162">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="db576-163">Os métodos virtuais e abstratos que são introduzidos em classes base ou interfaces, e substituídos ou implementados em uma classe de segurança crítica são transparentes por padrão.</span><span class="sxs-lookup"><span data-stu-id="db576-163">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="db576-164">Eles devem ser identificados como `SecuritySafeCritical` ou `SecurityCritical` .</span><span class="sxs-lookup"><span data-stu-id="db576-164">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="db576-165">`SecuritySafeCritical`: O tipo ou o membro é de segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="db576-165">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="db576-166">No entanto, o tipo ou membro pode ser chamado de código transparente (parcialmente confiável) e é compatível como qualquer outro código crítico.</span><span class="sxs-lookup"><span data-stu-id="db576-166">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="db576-167">O código deve ser auditado quanto à segurança.</span><span class="sxs-lookup"><span data-stu-id="db576-167">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="db576-168">Substituir Padrões</span><span class="sxs-lookup"><span data-stu-id="db576-168">Override Patterns</span></span>

<span data-ttu-id="db576-169">A tabela a seguir mostra as substituições de método permitidas para transparência de nível 2.</span><span class="sxs-lookup"><span data-stu-id="db576-169">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="db576-170">Membro de interface/virtual base</span><span class="sxs-lookup"><span data-stu-id="db576-170">Base virtual/interface member</span></span>|<span data-ttu-id="db576-171">Substituição/interface</span><span class="sxs-lookup"><span data-stu-id="db576-171">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="db576-172">Regras de Herança</span><span class="sxs-lookup"><span data-stu-id="db576-172">Inheritance Rules</span></span>

<span data-ttu-id="db576-173">Nesta seção, a seguinte ordem é atribuída a `Transparent` , `Critical` e a `SafeCritical` código com base no acesso e nos recursos:</span><span class="sxs-lookup"><span data-stu-id="db576-173">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="db576-174">Regras para tipos: indo da esquerda para a direita, o acesso se torna mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="db576-174">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="db576-175">Os tipos derivados devem ser pelo menos tão restritivos quanto o tipo base.</span><span class="sxs-lookup"><span data-stu-id="db576-175">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="db576-176">Regras para métodos: métodos derivados não podem alterar a acessibilidade do método base.</span><span class="sxs-lookup"><span data-stu-id="db576-176">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="db576-177">Para o comportamento padrão, todos os métodos derivados que não são anotados são `Transparent` .</span><span class="sxs-lookup"><span data-stu-id="db576-177">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="db576-178">Derivações de tipos críticos causam uma exceção a ser gerada se o método substituído não for anotado explicitamente como `SecurityCritical` .</span><span class="sxs-lookup"><span data-stu-id="db576-178">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="db576-179">A tabela a seguir mostra os padrões de herança de tipo permitidos.</span><span class="sxs-lookup"><span data-stu-id="db576-179">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="db576-180">Classe base</span><span class="sxs-lookup"><span data-stu-id="db576-180">Base class</span></span>|<span data-ttu-id="db576-181">A classe derivada pode ser</span><span class="sxs-lookup"><span data-stu-id="db576-181">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="db576-182">A tabela a seguir mostra os padrões de herança de tipo não permitido.</span><span class="sxs-lookup"><span data-stu-id="db576-182">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="db576-183">Classe base</span><span class="sxs-lookup"><span data-stu-id="db576-183">Base class</span></span>|<span data-ttu-id="db576-184">A classe derivada não pode ser</span><span class="sxs-lookup"><span data-stu-id="db576-184">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="db576-185">A tabela a seguir mostra os padrões de herança de método permitidos.</span><span class="sxs-lookup"><span data-stu-id="db576-185">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="db576-186">Método base</span><span class="sxs-lookup"><span data-stu-id="db576-186">Base method</span></span>|<span data-ttu-id="db576-187">O método derivado pode ser</span><span class="sxs-lookup"><span data-stu-id="db576-187">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="db576-188">A tabela a seguir mostra os padrões de herança de método não permitido.</span><span class="sxs-lookup"><span data-stu-id="db576-188">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="db576-189">Método base</span><span class="sxs-lookup"><span data-stu-id="db576-189">Base method</span></span>|<span data-ttu-id="db576-190">O método derivado não pode ser</span><span class="sxs-lookup"><span data-stu-id="db576-190">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="db576-191">Essas regras de herança se aplicam a tipos e membros de nível 2.</span><span class="sxs-lookup"><span data-stu-id="db576-191">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="db576-192">Os tipos em assemblies de nível 1 podem herdar de membros e tipos de segurança de nível 2-críticos.</span><span class="sxs-lookup"><span data-stu-id="db576-192">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="db576-193">Portanto, os tipos de nível 2 e os membros devem ter demandas de herança separadas para herdeiros de nível 1.</span><span class="sxs-lookup"><span data-stu-id="db576-193">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="db576-194">Informações Adicionais e Regras</span><span class="sxs-lookup"><span data-stu-id="db576-194">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="db576-195">Suporte LinkDemand</span><span class="sxs-lookup"><span data-stu-id="db576-195">LinkDemand Support</span></span>

<span data-ttu-id="db576-196">O modelo de transparência nível 2 substitui o <xref:System.Security.Permissions.SecurityAction.LinkDemand> pelo <xref:System.Security.SecurityCriticalAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="db576-196">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="db576-197">No código herdado (nível 1), um <xref:System.Security.Permissions.SecurityAction.LinkDemand> é automaticamente tratado como um <xref:System.Security.Permissions.SecurityAction.Demand> .</span><span class="sxs-lookup"><span data-stu-id="db576-197">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="db576-198">Reflexão</span><span class="sxs-lookup"><span data-stu-id="db576-198">Reflection</span></span>

<span data-ttu-id="db576-199">Invocar um método crítico ou ler um campo crítico dispara uma demanda de confiança total (assim como se você estivesse invocando um método ou um campo particular).</span><span class="sxs-lookup"><span data-stu-id="db576-199">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="db576-200">Portanto, o código de confiança total pode invocar um método crítico, enquanto o código de confiança parcial não pode.</span><span class="sxs-lookup"><span data-stu-id="db576-200">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="db576-201">As propriedades a seguir foram adicionadas ao <xref:System.Reflection> namespace para determinar se o tipo, o método ou o campo é `SecurityCritical` , `SecuritySafeCritical` , ou `SecurityTransparent` : <xref:System.Type.IsSecurityCritical%2A> , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A> .</span><span class="sxs-lookup"><span data-stu-id="db576-201">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="db576-202">Use essas propriedades para determinar a transparência usando reflexão em vez de verificar a presença do atributo.</span><span class="sxs-lookup"><span data-stu-id="db576-202">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="db576-203">As regras de transparência são complexas e a verificação do atributo pode não ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="db576-203">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="db576-204">Um `SafeCritical` método retorna `true` para <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , porque `SafeCritical` é realmente crítico (ele tem os mesmos recursos que o código crítico, mas pode ser chamado a partir do código Transparent).</span><span class="sxs-lookup"><span data-stu-id="db576-204">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="db576-205">Métodos dinâmicos herdam a transparência dos módulos aos quais eles estão anexados; Eles não herdam a transparência do tipo (se estiverem anexados a um tipo).</span><span class="sxs-lookup"><span data-stu-id="db576-205">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="db576-206">Ignorar Verificação em Confiança Total</span><span class="sxs-lookup"><span data-stu-id="db576-206">Skip Verification in Full Trust</span></span>

<span data-ttu-id="db576-207">Você pode ignorar a verificação de assemblies transparentes totalmente confiáveis definindo a <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade como `true` no <xref:System.Security.SecurityRulesAttribute> atributo:</span><span class="sxs-lookup"><span data-stu-id="db576-207">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="db576-208">A <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade é `false` por padrão, portanto, a propriedade deve ser definida como `true` para ignorar a verificação.</span><span class="sxs-lookup"><span data-stu-id="db576-208">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="db576-209">Isso deve ser feito apenas para fins de otimização.</span><span class="sxs-lookup"><span data-stu-id="db576-209">This should be done for optimization purposes only.</span></span> <span data-ttu-id="db576-210">Você deve garantir que o código transparent no assembly seja verificável usando a `transparent` opção na [ferramenta PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="db576-210">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db576-211">Confira também</span><span class="sxs-lookup"><span data-stu-id="db576-211">See also</span></span>

- [<span data-ttu-id="db576-212">Segurança-código Transparent, nível 1</span><span class="sxs-lookup"><span data-stu-id="db576-212">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="db576-213">Alterações de segurança</span><span class="sxs-lookup"><span data-stu-id="db576-213">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
