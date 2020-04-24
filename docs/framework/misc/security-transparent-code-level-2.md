---
title: Código transparente de segurança, nível 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645726"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="9131d-102">Código transparente de segurança, nível 2</span><span class="sxs-lookup"><span data-stu-id="9131d-102">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="9131d-103">A transparência nível 2 foi introduzida no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="9131d-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="9131d-104">Os três princípios deste modelo são código transparente, código crítico de segurança e código crítico de segurança.</span><span class="sxs-lookup"><span data-stu-id="9131d-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="9131d-105">O código transparente, incluindo o código que está sendo executado como confiança total, pode chamar outro código transparente ou código crítico de segurança apenas.</span><span class="sxs-lookup"><span data-stu-id="9131d-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="9131d-106">Ele só pode executar ações permitidas pelo conjunto de permissão de confiança parcial do domínio (se existir).</span><span class="sxs-lookup"><span data-stu-id="9131d-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="9131d-107">O código transparente não pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9131d-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="9131d-108">Realizar <xref:System.Security.CodeAccessPermission.Assert%2A> uma ou elevação de privilégios.</span><span class="sxs-lookup"><span data-stu-id="9131d-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="9131d-109">Contenha código inseguro ou inverificável.</span><span class="sxs-lookup"><span data-stu-id="9131d-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="9131d-110">Chame diretamente código crítico.</span><span class="sxs-lookup"><span data-stu-id="9131d-110">Directly call critical code.</span></span>

  - <span data-ttu-id="9131d-111">Ligue para código ou <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> código nativo com o atributo.</span><span class="sxs-lookup"><span data-stu-id="9131d-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="9131d-112">Ligue para um membro <xref:System.Security.Permissions.SecurityAction.LinkDemand>que é protegido por um .</span><span class="sxs-lookup"><span data-stu-id="9131d-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="9131d-113">Herdar de tipos críticos.</span><span class="sxs-lookup"><span data-stu-id="9131d-113">Inherit from critical types.</span></span>

  <span data-ttu-id="9131d-114">Além disso, métodos transparentes não podem substituir métodos virtuais críticos ou implementar métodos críticos de interface.</span><span class="sxs-lookup"><span data-stu-id="9131d-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="9131d-115">O código de segurança é totalmente confiável, mas pode ser callable por código transparente.</span><span class="sxs-lookup"><span data-stu-id="9131d-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="9131d-116">Expõe uma área de superfície limitada de código de confiança total; correção e verificações de segurança acontecem em código de segurança-crítica.</span><span class="sxs-lookup"><span data-stu-id="9131d-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="9131d-117">O código crítico de segurança pode chamar qualquer código e é totalmente confiável, mas não pode ser chamado por código transparente.</span><span class="sxs-lookup"><span data-stu-id="9131d-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="9131d-118">Exemplos de Uso e Comportamentos</span><span class="sxs-lookup"><span data-stu-id="9131d-118">Usage Examples and Behaviors</span></span>

<span data-ttu-id="9131d-119">Para especificar as regras do Quadro .NET 4 (transparência nível 2), use a seguinte anotação para uma montagem:</span><span class="sxs-lookup"><span data-stu-id="9131d-119">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="9131d-120">Para bloquear as regras do Quadro .NET 2.0 (transparência nível 1), use a seguinte anotação:</span><span class="sxs-lookup"><span data-stu-id="9131d-120">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="9131d-121">Se você não anotar um conjunto, as regras do .NET Framework 4 serão usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="9131d-121">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="9131d-122">No entanto, a melhor prática <xref:System.Security.SecurityRulesAttribute> recomendada é usar o atributo em vez de depender do padrão.</span><span class="sxs-lookup"><span data-stu-id="9131d-122">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="9131d-123">Anotação em toda a montagem</span><span class="sxs-lookup"><span data-stu-id="9131d-123">Assembly-wide Annotation</span></span>

<span data-ttu-id="9131d-124">As seguintes regras aplicam-se ao uso de atributos no nível de montagem:</span><span class="sxs-lookup"><span data-stu-id="9131d-124">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="9131d-125">Sem atributos: Se você não especificar nenhum atributo, o tempo de execução interpretará todo o código como crítico de segurança, exceto quando ser crítico de segurança viola uma regra de herança (por exemplo, ao sobrepor ou implementar um método virtual ou de interface transparente).</span><span class="sxs-lookup"><span data-stu-id="9131d-125">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="9131d-126">Nesses casos, os métodos são seguros e críticos.</span><span class="sxs-lookup"><span data-stu-id="9131d-126">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="9131d-127">Especificar nenhum atributo faz com que o tempo de execução do idioma comum determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="9131d-127">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="9131d-128">`SecurityTransparent`: Todos os códigos são transparentes; toda a assembléia não fará nada privilegiado ou inseguro.</span><span class="sxs-lookup"><span data-stu-id="9131d-128">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="9131d-129">`SecurityCritical`: Todo o código introduzido por tipos nesta montagem é crítico; todos os outros códigos são transparentes.</span><span class="sxs-lookup"><span data-stu-id="9131d-129">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="9131d-130">Este cenário é semelhante ao não especificar nenhum atributo; no entanto, o tempo de execução do idioma comum não determina automaticamente as regras de transparência.</span><span class="sxs-lookup"><span data-stu-id="9131d-130">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="9131d-131">Por exemplo, se você substituir um método virtual ou abstrato ou implementar um método de interface, por padrão, esse método é transparente.</span><span class="sxs-lookup"><span data-stu-id="9131d-131">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="9131d-132">Você deve anotar explicitamente o `SecurityCritical` método `SecuritySafeCritical`como ou; caso contrário, <xref:System.TypeLoadException> um será jogado na hora da carga.</span><span class="sxs-lookup"><span data-stu-id="9131d-132">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="9131d-133">Esta regra também se aplica quando tanto a classe base quanto a classe derivada estão na mesma montagem.</span><span class="sxs-lookup"><span data-stu-id="9131d-133">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="9131d-134">`AllowPartiallyTrustedCallers`(somente nível 2): Todos os padrões de código são transparentes.</span><span class="sxs-lookup"><span data-stu-id="9131d-134">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="9131d-135">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="9131d-135">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="9131d-136">A tabela a seguir compara o comportamento do nível de montagem para o Nível 2 com o Nível 1.</span><span class="sxs-lookup"><span data-stu-id="9131d-136">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="9131d-137">Atributo de assembly</span><span class="sxs-lookup"><span data-stu-id="9131d-137">Assembly attribute</span></span>|<span data-ttu-id="9131d-138">Nível 2</span><span class="sxs-lookup"><span data-stu-id="9131d-138">Level 2</span></span>|<span data-ttu-id="9131d-139">Nível 1</span><span class="sxs-lookup"><span data-stu-id="9131d-139">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="9131d-140">Nenhum atributo em uma assembléia parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="9131d-140">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="9131d-141">Os tipos e membros são transparentes por padrão, mas podem ser críticos à segurança ou críticos à segurança.</span><span class="sxs-lookup"><span data-stu-id="9131d-141">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="9131d-142">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="9131d-142">All types and members are transparent.</span></span>|
|<span data-ttu-id="9131d-143">Nenhum atributo</span><span class="sxs-lookup"><span data-stu-id="9131d-143">No attribute</span></span>|<span data-ttu-id="9131d-144">Especificar nenhum atributo faz com que o tempo de execução do idioma comum determine as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="9131d-144">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="9131d-145">Todos os tipos e membros são críticos à segurança, exceto quando ser crítico de segurança viola uma regra de herança.</span><span class="sxs-lookup"><span data-stu-id="9131d-145">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="9131d-146">Em uma montagem totalmente confiável (no cache de montagem `AppDomain`global ou identificada como total confiança no ) todos os tipos são transparentes e todos os membros são críticos à segurança.</span><span class="sxs-lookup"><span data-stu-id="9131d-146">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="9131d-147">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="9131d-147">All types and members are transparent.</span></span>|<span data-ttu-id="9131d-148">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="9131d-148">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="9131d-149">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9131d-149">Not applicable.</span></span>|<span data-ttu-id="9131d-150">Todos os tipos e membros são críticos à segurança.</span><span class="sxs-lookup"><span data-stu-id="9131d-150">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="9131d-151">Todo o código introduzido por tipos neste conjunto é crítico; todos os outros códigos são transparentes.</span><span class="sxs-lookup"><span data-stu-id="9131d-151">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="9131d-152">Se você substituir um método virtual ou abstrato ou implementar um método `SecurityCritical` de `SecuritySafeCritical`interface, você deve anotar explicitamente o método como ou .</span><span class="sxs-lookup"><span data-stu-id="9131d-152">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="9131d-153">Todos os códigos são padrão transparentes.</span><span class="sxs-lookup"><span data-stu-id="9131d-153">All code defaults to transparent.</span></span> <span data-ttu-id="9131d-154">No entanto, tipos individuais e membros podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="9131d-154">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="9131d-155">Tipo e Anotação do Membro</span><span class="sxs-lookup"><span data-stu-id="9131d-155">Type and Member Annotation</span></span>

<span data-ttu-id="9131d-156">Os atributos de segurança aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="9131d-156">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="9131d-157">No entanto, eles não se aplicam a substituições virtuais ou abstratas da classe base ou implementações de interface.</span><span class="sxs-lookup"><span data-stu-id="9131d-157">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="9131d-158">As seguintes regras aplicam-se ao uso de atributos no tipo e no nível do membro:</span><span class="sxs-lookup"><span data-stu-id="9131d-158">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="9131d-159">`SecurityCritical`: O tipo ou membro é crítico e só pode ser chamado por código de confiança total.</span><span class="sxs-lookup"><span data-stu-id="9131d-159">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="9131d-160">Os métodos introduzidos em um tipo crítico de segurança são críticos.</span><span class="sxs-lookup"><span data-stu-id="9131d-160">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9131d-161">Os métodos virtuais e abstratos que são introduzidos em classes ou interfaces básicas e substituídos ou implementados em uma classe crítica de segurança são transparentes por padrão.</span><span class="sxs-lookup"><span data-stu-id="9131d-161">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="9131d-162">Eles devem ser `SecuritySafeCritical` identificados como `SecurityCritical`ou.</span><span class="sxs-lookup"><span data-stu-id="9131d-162">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="9131d-163">`SecuritySafeCritical`: O tipo ou membro é seguro-crítico.</span><span class="sxs-lookup"><span data-stu-id="9131d-163">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="9131d-164">No entanto, o tipo ou membro pode ser chamado de código transparente (parcialmente confiável) e é tão capaz quanto qualquer outro código crítico.</span><span class="sxs-lookup"><span data-stu-id="9131d-164">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="9131d-165">O código deve ser auditado por segurança.</span><span class="sxs-lookup"><span data-stu-id="9131d-165">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="9131d-166">Substituir Padrões</span><span class="sxs-lookup"><span data-stu-id="9131d-166">Override Patterns</span></span>

<span data-ttu-id="9131d-167">A tabela a seguir mostra que o método substitui permitido a transparência nível 2.</span><span class="sxs-lookup"><span data-stu-id="9131d-167">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="9131d-168">Membro de interface/virtual base</span><span class="sxs-lookup"><span data-stu-id="9131d-168">Base virtual/interface member</span></span>|<span data-ttu-id="9131d-169">Substituição/interface</span><span class="sxs-lookup"><span data-stu-id="9131d-169">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="9131d-170">Regras de Herança</span><span class="sxs-lookup"><span data-stu-id="9131d-170">Inheritance Rules</span></span>

<span data-ttu-id="9131d-171">Nesta seção, a seguinte ordem `Transparent` `Critical`é `SafeCritical` atribuída a , e código com base no acesso e recursos:</span><span class="sxs-lookup"><span data-stu-id="9131d-171">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="9131d-172">Regras para tipos: Indo da esquerda para a direita, o acesso se torna mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="9131d-172">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="9131d-173">Os tipos derivados devem ser pelo menos tão restritivos quanto o tipo de base.</span><span class="sxs-lookup"><span data-stu-id="9131d-173">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="9131d-174">Regras para métodos: Os métodos derivados não podem alterar a acessibilidade do método base.</span><span class="sxs-lookup"><span data-stu-id="9131d-174">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="9131d-175">Para o comportamento padrão, todos os métodos derivados que não são anotados são `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="9131d-175">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="9131d-176">Derivativos de tipos críticos fazem com que uma exceção seja lançada `SecurityCritical`se o método substituído não for explicitamente anotado como .</span><span class="sxs-lookup"><span data-stu-id="9131d-176">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="9131d-177">A tabela a seguir mostra os padrões de herança do tipo permitidos.</span><span class="sxs-lookup"><span data-stu-id="9131d-177">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="9131d-178">Classe base</span><span class="sxs-lookup"><span data-stu-id="9131d-178">Base class</span></span>|<span data-ttu-id="9131d-179">Classe derivada pode ser</span><span class="sxs-lookup"><span data-stu-id="9131d-179">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="9131d-180">A tabela a seguir mostra os padrões de herança do tipo proibidos.</span><span class="sxs-lookup"><span data-stu-id="9131d-180">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="9131d-181">Classe base</span><span class="sxs-lookup"><span data-stu-id="9131d-181">Base class</span></span>|<span data-ttu-id="9131d-182">Classe derivada não pode ser</span><span class="sxs-lookup"><span data-stu-id="9131d-182">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="9131d-183">A tabela a seguir mostra os padrões de herança do método permitido.</span><span class="sxs-lookup"><span data-stu-id="9131d-183">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="9131d-184">Método base</span><span class="sxs-lookup"><span data-stu-id="9131d-184">Base method</span></span>|<span data-ttu-id="9131d-185">Método derivado pode ser</span><span class="sxs-lookup"><span data-stu-id="9131d-185">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="9131d-186">A tabela a seguir mostra os padrões de herança do método proibido.</span><span class="sxs-lookup"><span data-stu-id="9131d-186">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="9131d-187">Método base</span><span class="sxs-lookup"><span data-stu-id="9131d-187">Base method</span></span>|<span data-ttu-id="9131d-188">Método derivado não pode ser</span><span class="sxs-lookup"><span data-stu-id="9131d-188">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="9131d-189">Essas regras de herança se aplicam aos tipos e membros do nível 2.</span><span class="sxs-lookup"><span data-stu-id="9131d-189">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="9131d-190">Os tipos em conjuntos de nível 1 podem herdar de tipos e membros críticos de segurança nível 2.</span><span class="sxs-lookup"><span data-stu-id="9131d-190">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="9131d-191">Portanto, os tipos de nível 2 e os membros devem ter demandas de herança separadas para os herdeiros do nível 1.</span><span class="sxs-lookup"><span data-stu-id="9131d-191">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="9131d-192">Informações Adicionais e Regras</span><span class="sxs-lookup"><span data-stu-id="9131d-192">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="9131d-193">Suporte LinkDemand</span><span class="sxs-lookup"><span data-stu-id="9131d-193">LinkDemand Support</span></span>

<span data-ttu-id="9131d-194">O modelo de transparência <xref:System.Security.Permissions.SecurityAction.LinkDemand> nível <xref:System.Security.SecurityCriticalAttribute> 2 substitui o atributo.</span><span class="sxs-lookup"><span data-stu-id="9131d-194">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="9131d-195">No código legado (nível <xref:System.Security.Permissions.SecurityAction.LinkDemand> 1), a é <xref:System.Security.Permissions.SecurityAction.Demand>automaticamente tratada como a .</span><span class="sxs-lookup"><span data-stu-id="9131d-195">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="9131d-196">Reflexão</span><span class="sxs-lookup"><span data-stu-id="9131d-196">Reflection</span></span>

<span data-ttu-id="9131d-197">Invocar um método crítico ou ler um campo crítico desencadeia uma demanda por confiança total (como se você estivesse invocando um método ou campo privado).</span><span class="sxs-lookup"><span data-stu-id="9131d-197">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="9131d-198">Portanto, o código de confiança total pode invocar um método crítico, enquanto o código de confiança parcial não pode.</span><span class="sxs-lookup"><span data-stu-id="9131d-198">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="9131d-199">As seguintes propriedades foram <xref:System.Reflection> adicionadas ao namespace para determinar `SecurityCritical`se `SecuritySafeCritical`o `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A>tipo, método ou campo é, ou : , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="9131d-199">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="9131d-200">Use essas propriedades para determinar a transparência usando a reflexão em vez de verificar a presença do atributo.</span><span class="sxs-lookup"><span data-stu-id="9131d-200">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="9131d-201">As regras de transparência são complexas, e a verificação do atributo pode não ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="9131d-201">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="9131d-202">Um `SafeCritical` método `true` retorna <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>para `SafeCritical` ambos e, porque é realmente crítico (ele tem as mesmas capacidades que o código crítico, mas pode ser chamado de código transparente).</span><span class="sxs-lookup"><span data-stu-id="9131d-202">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="9131d-203">Os métodos dinâmicos herdam a transparência dos módulos a que estão conectados; eles não herdam a transparência do tipo (se estiverem ligados a um tipo).</span><span class="sxs-lookup"><span data-stu-id="9131d-203">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="9131d-204">Ignorar Verificação em Confiança Total</span><span class="sxs-lookup"><span data-stu-id="9131d-204">Skip Verification in Full Trust</span></span>

<span data-ttu-id="9131d-205">Você pode pular a verificação para <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> conjuntos `true` transparentes totalmente confiáveis definindo a propriedade no atributo: <xref:System.Security.SecurityRulesAttribute></span><span class="sxs-lookup"><span data-stu-id="9131d-205">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="9131d-206">A <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade `false` é por padrão, então a `true` propriedade deve ser definida para pular a verificação.</span><span class="sxs-lookup"><span data-stu-id="9131d-206">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="9131d-207">Isso deve ser feito apenas para fins de otimização.</span><span class="sxs-lookup"><span data-stu-id="9131d-207">This should be done for optimization purposes only.</span></span> <span data-ttu-id="9131d-208">Você deve garantir que o código transparente no conjunto `transparent` seja verificável usando a opção na [ferramenta PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9131d-208">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9131d-209">Confira também</span><span class="sxs-lookup"><span data-stu-id="9131d-209">See also</span></span>

- [<span data-ttu-id="9131d-210">Código transparente de segurança, nível 1</span><span class="sxs-lookup"><span data-stu-id="9131d-210">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="9131d-211">Alterações de segurança</span><span class="sxs-lookup"><span data-stu-id="9131d-211">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
