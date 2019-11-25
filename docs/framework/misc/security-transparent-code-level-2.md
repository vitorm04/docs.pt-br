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
ms.openlocfilehash: ea782b346f6c53664a8aeb736c7d7a4509d83985
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974940"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="63528-102">Código transparente de segurança, nível 2</span><span class="sxs-lookup"><span data-stu-id="63528-102">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="63528-103">A transparência de nível 2 foi introduzida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="63528-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="63528-104">As três filosofias desse modelo são código Transparent, segurança – código crítico e com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="63528-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="63528-105">O código Transparent, incluindo o código que está sendo executado como confiança total, pode chamar outros códigos transparentes ou somente com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="63528-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="63528-106">Ele só pode executar ações permitidas pelo conjunto de permissões de confiança parcial do domínio (se houver).</span><span class="sxs-lookup"><span data-stu-id="63528-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="63528-107">O código transparent não pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="63528-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="63528-108">Execute um <xref:System.Security.CodeAccessPermission.Assert%2A> ou elevação de privilégio.</span><span class="sxs-lookup"><span data-stu-id="63528-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="63528-109">Conter código não seguro ou não verificável.</span><span class="sxs-lookup"><span data-stu-id="63528-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="63528-110">Chame diretamente o código crítico.</span><span class="sxs-lookup"><span data-stu-id="63528-110">Directly call critical code.</span></span>

  - <span data-ttu-id="63528-111">Chame código nativo ou código com o atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63528-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="63528-112">Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="63528-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="63528-113">Herdar de tipos críticos.</span><span class="sxs-lookup"><span data-stu-id="63528-113">Inherit from critical types.</span></span>

  <span data-ttu-id="63528-114">Além disso, os métodos Transparent não podem substituir métodos virtuais críticos nem implementar métodos de interface críticos.</span><span class="sxs-lookup"><span data-stu-id="63528-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="63528-115">O código crítico seguro é totalmente confiável, mas é possível chamá-lo por código Transparent.</span><span class="sxs-lookup"><span data-stu-id="63528-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="63528-116">Ele expõe uma área de superfície limitada de código de confiança total; a correção e as verificações de segurança ocorrem em código crítico seguro.</span><span class="sxs-lookup"><span data-stu-id="63528-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="63528-117">O código de segurança crítica pode chamar qualquer código e é totalmente confiável, mas não pode ser chamado pelo código Transparent.</span><span class="sxs-lookup"><span data-stu-id="63528-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="63528-118">Exemplos de Uso e Comportamentos</span><span class="sxs-lookup"><span data-stu-id="63528-118">Usage Examples and Behaviors</span></span>

<span data-ttu-id="63528-119">Para especificar .NET Framework regras de 4 (transparência de nível 2), use a seguinte anotação para um assembly:</span><span class="sxs-lookup"><span data-stu-id="63528-119">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="63528-120">Para bloquear as regras do .NET Framework 2,0 (transparência de nível 1), use a seguinte anotação:</span><span class="sxs-lookup"><span data-stu-id="63528-120">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="63528-121">Se você não anotar um assembly, as regras .NET Framework 4 serão usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="63528-121">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="63528-122">No entanto, a prática recomendada é usar o atributo <xref:System.Security.SecurityRulesAttribute> em vez de dependendo do padrão.</span><span class="sxs-lookup"><span data-stu-id="63528-122">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="63528-123">Anotação em todo o assembly</span><span class="sxs-lookup"><span data-stu-id="63528-123">Assembly-wide Annotation</span></span>

<span data-ttu-id="63528-124">As regras a seguir se aplicam ao uso de atributos no nível do assembly:</span><span class="sxs-lookup"><span data-stu-id="63528-124">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="63528-125">Nenhum atributo: se você não especificar nenhum atributo, o tempo de execução interpretará todo o código como segurança crítica, exceto onde a segurança crítica viola uma regra de herança (por exemplo, ao substituir ou implementar um método de interface ou virtual transparente ).</span><span class="sxs-lookup"><span data-stu-id="63528-125">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="63528-126">Nesses casos, os métodos são de segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="63528-126">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="63528-127">Especificar nenhum atributo faz com que o Common Language Runtime determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="63528-127">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="63528-128">`SecurityTransparent`: todo o código é transparente; o assembly inteiro não fará nada privilegiado nem seguro.</span><span class="sxs-lookup"><span data-stu-id="63528-128">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="63528-129">`SecurityCritical`: todo o código introduzido por tipos neste assembly é crítico; todo o outro código é transparente.</span><span class="sxs-lookup"><span data-stu-id="63528-129">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="63528-130">Esse cenário é semelhante a não especificar nenhum atributo; no entanto, o Common Language Runtime não determina automaticamente as regras de transparência.</span><span class="sxs-lookup"><span data-stu-id="63528-130">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="63528-131">Por exemplo, se você substituir um método virtual ou abstract ou implementar um método de interface, por padrão, esse método será transparente.</span><span class="sxs-lookup"><span data-stu-id="63528-131">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="63528-132">Você deve anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`; caso contrário, uma <xref:System.TypeLoadException> será lançada no tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="63528-132">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="63528-133">Essa regra também se aplica quando a classe base e a classe derivada estão no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="63528-133">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="63528-134">`AllowPartiallyTrustedCallers` (somente nível 2): todos os padrões de código são transparentes.</span><span class="sxs-lookup"><span data-stu-id="63528-134">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="63528-135">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="63528-135">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="63528-136">A tabela a seguir compara o comportamento de nível de assembly para o nível 2 com o nível 1.</span><span class="sxs-lookup"><span data-stu-id="63528-136">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="63528-137">Atributo de assembly</span><span class="sxs-lookup"><span data-stu-id="63528-137">Assembly attribute</span></span>|<span data-ttu-id="63528-138">Nível 2</span><span class="sxs-lookup"><span data-stu-id="63528-138">Level 2</span></span>|<span data-ttu-id="63528-139">Nível 1</span><span class="sxs-lookup"><span data-stu-id="63528-139">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="63528-140">Nenhum atributo em um assembly parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="63528-140">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="63528-141">Os tipos e membros são, por padrão, transparentes, mas podem ser críticos para segurança ou com segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="63528-141">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="63528-142">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="63528-142">All types and members are transparent.</span></span>|
|<span data-ttu-id="63528-143">Nenhum atributo</span><span class="sxs-lookup"><span data-stu-id="63528-143">No attribute</span></span>|<span data-ttu-id="63528-144">Especificar nenhum atributo faz com que o Common Language Runtime determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="63528-144">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="63528-145">Todos os tipos e membros são críticos à segurança, exceto onde a segurança crítica viola uma regra de herança.</span><span class="sxs-lookup"><span data-stu-id="63528-145">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="63528-146">Em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`), todos os tipos são transparentes e todos os membros são críticos à segurança.</span><span class="sxs-lookup"><span data-stu-id="63528-146">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="63528-147">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="63528-147">All types and members are transparent.</span></span>|<span data-ttu-id="63528-148">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="63528-148">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="63528-149">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="63528-149">Not applicable.</span></span>|<span data-ttu-id="63528-150">Todos os tipos e membros são críticos para a segurança.</span><span class="sxs-lookup"><span data-stu-id="63528-150">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="63528-151">Todo o código introduzido por tipos neste assembly é crítico; todo o outro código é transparente.</span><span class="sxs-lookup"><span data-stu-id="63528-151">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="63528-152">Se você substituir um método virtual ou abstract ou implementar um método de interface, você deverá anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="63528-152">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="63528-153">Todos os padrões de código são transparentes.</span><span class="sxs-lookup"><span data-stu-id="63528-153">All code defaults to transparent.</span></span> <span data-ttu-id="63528-154">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="63528-154">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="63528-155">Tipo e Anotação do Membro</span><span class="sxs-lookup"><span data-stu-id="63528-155">Type and Member Annotation</span></span>

<span data-ttu-id="63528-156">Os atributos de segurança que são aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="63528-156">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="63528-157">No entanto, eles não se aplicam a substituições virtuais ou abstratas da classe base ou implementações de interface.</span><span class="sxs-lookup"><span data-stu-id="63528-157">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="63528-158">As regras a seguir se aplicam ao uso de atributos no nível de tipo e de membro:</span><span class="sxs-lookup"><span data-stu-id="63528-158">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="63528-159">`SecurityCritical`: o tipo ou membro é crítico e pode ser chamado somente pelo código de confiança total.</span><span class="sxs-lookup"><span data-stu-id="63528-159">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="63528-160">Os métodos que são introduzidos em um tipo de segurança crítica são críticos.</span><span class="sxs-lookup"><span data-stu-id="63528-160">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="63528-161">Os métodos virtuais e abstratos que são introduzidos em classes base ou interfaces, e substituídos ou implementados em uma classe de segurança crítica são transparentes por padrão.</span><span class="sxs-lookup"><span data-stu-id="63528-161">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="63528-162">Eles devem ser identificados como `SecuritySafeCritical` ou `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="63528-162">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="63528-163">`SecuritySafeCritical`: o tipo ou o membro é crítico e seguro.</span><span class="sxs-lookup"><span data-stu-id="63528-163">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="63528-164">No entanto, o tipo ou membro pode ser chamado de código transparente (parcialmente confiável) e é compatível como qualquer outro código crítico.</span><span class="sxs-lookup"><span data-stu-id="63528-164">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="63528-165">O código deve ser auditado quanto à segurança.</span><span class="sxs-lookup"><span data-stu-id="63528-165">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="63528-166">Substituir Padrões</span><span class="sxs-lookup"><span data-stu-id="63528-166">Override Patterns</span></span>

<span data-ttu-id="63528-167">A tabela a seguir mostra as substituições de método permitidas para transparência de nível 2.</span><span class="sxs-lookup"><span data-stu-id="63528-167">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="63528-168">Membro de interface/virtual base</span><span class="sxs-lookup"><span data-stu-id="63528-168">Base virtual/interface member</span></span>|<span data-ttu-id="63528-169">Substituição/interface</span><span class="sxs-lookup"><span data-stu-id="63528-169">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="63528-170">Regras de Herança</span><span class="sxs-lookup"><span data-stu-id="63528-170">Inheritance Rules</span></span>

<span data-ttu-id="63528-171">Nesta seção, a seguinte ordem é atribuída a `Transparent`, `Critical`e `SafeCritical` código com base no acesso e nos recursos:</span><span class="sxs-lookup"><span data-stu-id="63528-171">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="63528-172">Regras para tipos: indo da esquerda para a direita, o acesso se torna mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="63528-172">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="63528-173">Os tipos derivados devem ser pelo menos tão restritivos quanto o tipo base.</span><span class="sxs-lookup"><span data-stu-id="63528-173">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="63528-174">Regras para métodos: métodos derivados não podem alterar a acessibilidade do método base.</span><span class="sxs-lookup"><span data-stu-id="63528-174">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="63528-175">Para o comportamento padrão, todos os métodos derivados que não são anotados são `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="63528-175">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="63528-176">Derivações de tipos críticos causam uma exceção a ser gerada se o método substituído não for anotado explicitamente como `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="63528-176">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="63528-177">A tabela a seguir mostra os padrões de herança de tipo permitidos.</span><span class="sxs-lookup"><span data-stu-id="63528-177">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="63528-178">Classe base</span><span class="sxs-lookup"><span data-stu-id="63528-178">Base class</span></span>|<span data-ttu-id="63528-179">A classe derivada pode ser</span><span class="sxs-lookup"><span data-stu-id="63528-179">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="63528-180">A tabela a seguir mostra os padrões de herança de tipo não permitido.</span><span class="sxs-lookup"><span data-stu-id="63528-180">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="63528-181">Classe base</span><span class="sxs-lookup"><span data-stu-id="63528-181">Base class</span></span>|<span data-ttu-id="63528-182">A classe derivada não pode ser</span><span class="sxs-lookup"><span data-stu-id="63528-182">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="63528-183">A tabela a seguir mostra os padrões de herança de método permitidos.</span><span class="sxs-lookup"><span data-stu-id="63528-183">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="63528-184">Método base</span><span class="sxs-lookup"><span data-stu-id="63528-184">Base method</span></span>|<span data-ttu-id="63528-185">O método derivado pode ser</span><span class="sxs-lookup"><span data-stu-id="63528-185">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="63528-186">A tabela a seguir mostra os padrões de herança de método não permitido.</span><span class="sxs-lookup"><span data-stu-id="63528-186">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="63528-187">Método base</span><span class="sxs-lookup"><span data-stu-id="63528-187">Base method</span></span>|<span data-ttu-id="63528-188">O método derivado não pode ser</span><span class="sxs-lookup"><span data-stu-id="63528-188">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="63528-189">Essas regras de herança se aplicam a tipos e membros de nível 2.</span><span class="sxs-lookup"><span data-stu-id="63528-189">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="63528-190">Os tipos em assemblies de nível 1 podem herdar de membros e tipos de segurança de nível 2-críticos.</span><span class="sxs-lookup"><span data-stu-id="63528-190">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="63528-191">Portanto, os tipos de nível 2 e os membros devem ter demandas de herança separadas para herdeiros de nível 1.</span><span class="sxs-lookup"><span data-stu-id="63528-191">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="63528-192">Informações Adicionais e Regras</span><span class="sxs-lookup"><span data-stu-id="63528-192">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="63528-193">Suporte LinkDemand</span><span class="sxs-lookup"><span data-stu-id="63528-193">LinkDemand Support</span></span>

<span data-ttu-id="63528-194">O modelo de transparência nível 2 substitui o <xref:System.Security.Permissions.SecurityAction.LinkDemand> pelo atributo <xref:System.Security.SecurityCriticalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63528-194">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="63528-195">No código herdado (nível 1), um <xref:System.Security.Permissions.SecurityAction.LinkDemand> é tratado automaticamente como um <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="63528-195">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="63528-196">Reflexão</span><span class="sxs-lookup"><span data-stu-id="63528-196">Reflection</span></span>

<span data-ttu-id="63528-197">Invocar um método crítico ou ler um campo crítico dispara uma demanda de confiança total (assim como se você estivesse invocando um método ou um campo particular).</span><span class="sxs-lookup"><span data-stu-id="63528-197">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="63528-198">Portanto, o código de confiança total pode invocar um método crítico, enquanto o código de confiança parcial não pode.</span><span class="sxs-lookup"><span data-stu-id="63528-198">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="63528-199">As propriedades a seguir foram adicionadas ao namespace <xref:System.Reflection> para determinar se o tipo, o método ou o campo é `SecurityCritical`, `SecuritySafeCritical`ou `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="63528-199">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="63528-200">Use essas propriedades para determinar a transparência usando reflexão em vez de verificar a presença do atributo.</span><span class="sxs-lookup"><span data-stu-id="63528-200">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="63528-201">As regras de transparência são complexas e a verificação do atributo pode não ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="63528-201">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="63528-202">Um método `SafeCritical` retorna `true` para <xref:System.Type.IsSecurityCritical%2A> e <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, porque `SafeCritical` é realmente crítico (ele tem os mesmos recursos que o código crítico, mas pode ser chamado a partir do código Transparent).</span><span class="sxs-lookup"><span data-stu-id="63528-202">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="63528-203">Métodos dinâmicos herdam a transparência dos módulos aos quais eles estão anexados; Eles não herdam a transparência do tipo (se estiverem anexados a um tipo).</span><span class="sxs-lookup"><span data-stu-id="63528-203">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="63528-204">Ignorar Verificação em Confiança Total</span><span class="sxs-lookup"><span data-stu-id="63528-204">Skip Verification in Full Trust</span></span>

<span data-ttu-id="63528-205">Você pode ignorar a verificação de assemblies transparentes totalmente confiáveis definindo a propriedade <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> como `true` no atributo <xref:System.Security.SecurityRulesAttribute>:</span><span class="sxs-lookup"><span data-stu-id="63528-205">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="63528-206">A propriedade <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> é `false` por padrão, portanto, a propriedade deve ser definida como `true` para ignorar a verificação.</span><span class="sxs-lookup"><span data-stu-id="63528-206">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="63528-207">Isso deve ser feito apenas para fins de otimização.</span><span class="sxs-lookup"><span data-stu-id="63528-207">This should be done for optimization purposes only.</span></span> <span data-ttu-id="63528-208">Você deve garantir que o código transparent no assembly seja verificável usando a opção `transparent` na [ferramenta PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="63528-208">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63528-209">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63528-209">See also</span></span>

- [<span data-ttu-id="63528-210">Segurança-código Transparent, nível 1</span><span class="sxs-lookup"><span data-stu-id="63528-210">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="63528-211">Alterações de segurança</span><span class="sxs-lookup"><span data-stu-id="63528-211">Security Changes</span></span>](../security/security-changes.md)
