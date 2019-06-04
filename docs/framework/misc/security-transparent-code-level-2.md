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
ms.openlocfilehash: 36c3f139564b39555370cd5d41133f39c6b271bb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487837"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="2c95c-102">Código transparente de segurança, nível 2</span><span class="sxs-lookup"><span data-stu-id="2c95c-102">Security-Transparent Code, Level 2</span></span>

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="2c95c-103">Transparência de nível 2 foi introduzida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2c95c-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="2c95c-104">Os três tenets desse modelo são código transparente, código segurança-seguro-crítica e código de segurança crítica.</span><span class="sxs-lookup"><span data-stu-id="2c95c-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="2c95c-105">Código transparente, incluindo o código que está em execução em confiança total, pode chamar outro código transparente ou somente código segurança-seguro-crítica.</span><span class="sxs-lookup"><span data-stu-id="2c95c-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="2c95c-106">Ele só pode executar ações permitidas pela permissão de confiança parcial do domínio definido (se houver).</span><span class="sxs-lookup"><span data-stu-id="2c95c-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="2c95c-107">O código transparente não pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2c95c-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="2c95c-108">Executar um <xref:System.Security.CodeAccessPermission.Assert%2A> ou elevação de privilégio.</span><span class="sxs-lookup"><span data-stu-id="2c95c-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="2c95c-109">Contém código não seguro ou não verificável.</span><span class="sxs-lookup"><span data-stu-id="2c95c-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="2c95c-110">Chame um código crítico diretamente.</span><span class="sxs-lookup"><span data-stu-id="2c95c-110">Directly call critical code.</span></span>

  - <span data-ttu-id="2c95c-111">Chamar código nativo ou código com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="2c95c-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="2c95c-112">Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="2c95c-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="2c95c-113">Herda de tipos críticos.</span><span class="sxs-lookup"><span data-stu-id="2c95c-113">Inherit from critical types.</span></span>

  <span data-ttu-id="2c95c-114">Além disso, os métodos transparentes não podem substituir métodos virtuais críticos ou implementar métodos críticos da interface.</span><span class="sxs-lookup"><span data-stu-id="2c95c-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="2c95c-115">Código crítico de segurança é totalmente confiável, mas pode ser chamado pelo código transparent.</span><span class="sxs-lookup"><span data-stu-id="2c95c-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="2c95c-116">Ele expõe uma área da superfície limitada de código de confiança total; verificações de exatidão e segurança ocorrem no código crítico.</span><span class="sxs-lookup"><span data-stu-id="2c95c-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="2c95c-117">Código de segurança crítica pode chamar qualquer código e é totalmente confiável, mas ele não pode ser chamado pelo código transparent.</span><span class="sxs-lookup"><span data-stu-id="2c95c-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

<span data-ttu-id="2c95c-118">Esse tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="2c95c-118">This topic contains the following sections:</span></span>

- [<span data-ttu-id="2c95c-119">Exemplos de uso e comportamentos</span><span class="sxs-lookup"><span data-stu-id="2c95c-119">Usage Examples and Behaviors</span></span>](#examples)

- [<span data-ttu-id="2c95c-120">Substituir padrões</span><span class="sxs-lookup"><span data-stu-id="2c95c-120">Override Patterns</span></span>](#override)

- [<span data-ttu-id="2c95c-121">Regras de herança</span><span class="sxs-lookup"><span data-stu-id="2c95c-121">Inheritance Rules</span></span>](#inheritance)

- [<span data-ttu-id="2c95c-122">Informações adicionais e regras</span><span class="sxs-lookup"><span data-stu-id="2c95c-122">Additional Information and Rules</span></span>](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="2c95c-123">Exemplos de Uso e Comportamentos</span><span class="sxs-lookup"><span data-stu-id="2c95c-123">Usage Examples and Behaviors</span></span>

<span data-ttu-id="2c95c-124">Para especificar as regras do .NET Framework 4 (transparência de nível 2), use a anotação a seguir para um assembly:</span><span class="sxs-lookup"><span data-stu-id="2c95c-124">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="2c95c-125">Para bloquear nas regras do .NET Framework 2.0 (transparência de nível 1), use a anotação a seguir:</span><span class="sxs-lookup"><span data-stu-id="2c95c-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="2c95c-126">Se você não fazer anotações em um assembly, as regras do .NET Framework 4 são usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="2c95c-126">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="2c95c-127">No entanto, a prática recomendada é usar o <xref:System.Security.SecurityRulesAttribute> de atributo, em vez de dependendo do padrão.</span><span class="sxs-lookup"><span data-stu-id="2c95c-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="2c95c-128">Anotação de todo o assembly</span><span class="sxs-lookup"><span data-stu-id="2c95c-128">Assembly-wide Annotation</span></span>

<span data-ttu-id="2c95c-129">As seguintes regras se aplicam ao uso de atributos no nível de assembly:</span><span class="sxs-lookup"><span data-stu-id="2c95c-129">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="2c95c-130">Nenhum atributo: Se você não especificar todos os atributos, o tempo de execução interpreta todos os códigos como crítico de segurança, exceto onde sendo crítico para segurança viola uma regra de herança (por exemplo, quando a substituição ou implementando um transparente virtual ou o método de interface).</span><span class="sxs-lookup"><span data-stu-id="2c95c-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="2c95c-131">Nesses casos, os métodos são seguro-crítica.</span><span class="sxs-lookup"><span data-stu-id="2c95c-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="2c95c-132">Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="2c95c-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="2c95c-133">`SecurityTransparent`: Todo o código é transparente; todo o assembly não fará nada com privilégios ou que não é segura.</span><span class="sxs-lookup"><span data-stu-id="2c95c-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="2c95c-134">`SecurityCritical`: Todo o código que é introduzido pelos tipos neste assembly é essencial; todos os outros códigos é transparente.</span><span class="sxs-lookup"><span data-stu-id="2c95c-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="2c95c-135">Esse cenário é semelhante à especificação não todos os atributos; No entanto, o common language runtime não determina automaticamente as regras de transparência.</span><span class="sxs-lookup"><span data-stu-id="2c95c-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="2c95c-136">Por exemplo, se você substituir um método virtual ou abstract ou implementa um método de interface, por padrão, esse método é transparente.</span><span class="sxs-lookup"><span data-stu-id="2c95c-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="2c95c-137">Você deve anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`; caso contrário, um <xref:System.TypeLoadException> será lançada no tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="2c95c-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="2c95c-138">Essa regra também se aplica quando a classe base e a classe derivada estão no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="2c95c-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="2c95c-139">`AllowPartiallyTrustedCallers` (nível 2 somente): Todo o código padrão é transparente.</span><span class="sxs-lookup"><span data-stu-id="2c95c-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="2c95c-140">No entanto, os membros e tipos individuais podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="2c95c-140">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="2c95c-141">A tabela a seguir compara o comportamento de nível de assembly para o nível 2 com o nível 1.</span><span class="sxs-lookup"><span data-stu-id="2c95c-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="2c95c-142">Atributo de assembly</span><span class="sxs-lookup"><span data-stu-id="2c95c-142">Assembly attribute</span></span>|<span data-ttu-id="2c95c-143">Nível 2</span><span class="sxs-lookup"><span data-stu-id="2c95c-143">Level 2</span></span>|<span data-ttu-id="2c95c-144">Nível 1</span><span class="sxs-lookup"><span data-stu-id="2c95c-144">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="2c95c-145">Nenhum atributo em um assembly parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="2c95c-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="2c95c-146">Tipos e membros são por padrão transparente, mas podem ser crítico para segurança ou segurança-seguro-crítica.</span><span class="sxs-lookup"><span data-stu-id="2c95c-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="2c95c-147">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="2c95c-147">All types and members are transparent.</span></span>|
|<span data-ttu-id="2c95c-148">Nenhum atributo</span><span class="sxs-lookup"><span data-stu-id="2c95c-148">No attribute</span></span>|<span data-ttu-id="2c95c-149">Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você.</span><span class="sxs-lookup"><span data-stu-id="2c95c-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="2c95c-150">Todos os tipos e membros são críticos para segurança, exceto onde sendo crítico para segurança viola uma regra de herança.</span><span class="sxs-lookup"><span data-stu-id="2c95c-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="2c95c-151">Em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`) todos os tipos são transparentes e todos os membros são segurança-seguro-crítica.</span><span class="sxs-lookup"><span data-stu-id="2c95c-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="2c95c-152">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="2c95c-152">All types and members are transparent.</span></span>|<span data-ttu-id="2c95c-153">Todos os tipos e membros são transparentes.</span><span class="sxs-lookup"><span data-stu-id="2c95c-153">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="2c95c-154">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="2c95c-154">Not applicable.</span></span>|<span data-ttu-id="2c95c-155">Todos os tipos e membros são críticos para segurança.</span><span class="sxs-lookup"><span data-stu-id="2c95c-155">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="2c95c-156">Todo o código que é introduzido pelos tipos neste assembly é essencial; todos os outros códigos é transparente.</span><span class="sxs-lookup"><span data-stu-id="2c95c-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="2c95c-157">Se você substituir um método virtual ou abstract ou implementa um método de interface, você deve anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="2c95c-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="2c95c-158">Todo o código padrão é transparente.</span><span class="sxs-lookup"><span data-stu-id="2c95c-158">All code defaults to transparent.</span></span> <span data-ttu-id="2c95c-159">No entanto, os membros e tipos individuais podem ter outros atributos.</span><span class="sxs-lookup"><span data-stu-id="2c95c-159">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="2c95c-160">Tipo e Anotação do Membro</span><span class="sxs-lookup"><span data-stu-id="2c95c-160">Type and Member Annotation</span></span>

<span data-ttu-id="2c95c-161">Os atributos de segurança que são aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="2c95c-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="2c95c-162">No entanto, eles não se aplicam ao virtual ou abstract substitui das implementações de interface ou classe base.</span><span class="sxs-lookup"><span data-stu-id="2c95c-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="2c95c-163">As seguintes regras se aplicam ao uso de atributos no nível do tipo e membro:</span><span class="sxs-lookup"><span data-stu-id="2c95c-163">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="2c95c-164">`SecurityCritical`: O tipo ou membro é crítico e pode ser chamado somente pelo código de confiança total.</span><span class="sxs-lookup"><span data-stu-id="2c95c-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="2c95c-165">Métodos que são introduzidos em um tipo crítico de segurança são essenciais.</span><span class="sxs-lookup"><span data-stu-id="2c95c-165">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="2c95c-166">Métodos abstratos e virtuais que são introduzidos em interfaces ou classes base e substituídos ou implementados em uma classe de segurança críticas são transparentes por padrão.</span><span class="sxs-lookup"><span data-stu-id="2c95c-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="2c95c-167">Eles devem ser identificados como `SecuritySafeCritical` ou `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="2c95c-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="2c95c-168">`SecuritySafeCritical`: O tipo ou membro é crítico.</span><span class="sxs-lookup"><span data-stu-id="2c95c-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="2c95c-169">No entanto, o tipo ou membro pode ser chamado no código transparent de (parcialmente confiável) e é tão potentes quanto qualquer outro código crítico.</span><span class="sxs-lookup"><span data-stu-id="2c95c-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="2c95c-170">O código deve ser auditado para segurança.</span><span class="sxs-lookup"><span data-stu-id="2c95c-170">The code must be audited for security.</span></span>

[<span data-ttu-id="2c95c-171">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="2c95c-171">Back to top</span></span>](#top)

<a name="override"></a>

## <a name="override-patterns"></a><span data-ttu-id="2c95c-172">Substituir Padrões</span><span class="sxs-lookup"><span data-stu-id="2c95c-172">Override Patterns</span></span>

<span data-ttu-id="2c95c-173">A tabela a seguir mostra as substituições de método permitidas para a transparência de nível 2.</span><span class="sxs-lookup"><span data-stu-id="2c95c-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="2c95c-174">Membro de base virtuais/interface</span><span class="sxs-lookup"><span data-stu-id="2c95c-174">Base virtual/interface member</span></span>|<span data-ttu-id="2c95c-175">Substituição/interface</span><span class="sxs-lookup"><span data-stu-id="2c95c-175">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[<span data-ttu-id="2c95c-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="2c95c-176">Back to top</span></span>](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a><span data-ttu-id="2c95c-177">Regras de Herança</span><span class="sxs-lookup"><span data-stu-id="2c95c-177">Inheritance Rules</span></span>

<span data-ttu-id="2c95c-178">Nesta seção, a ordem a seguir é atribuída a `Transparent`, `Critical`, e `SafeCritical` código com base no acesso e recursos:</span><span class="sxs-lookup"><span data-stu-id="2c95c-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="2c95c-179">Regras para tipos: Saindo da esquerda para a direita, o acesso se torna mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="2c95c-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="2c95c-180">Tipos derivados devam ser, pelo menos, tão restritivos quanto o tipo base.</span><span class="sxs-lookup"><span data-stu-id="2c95c-180">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="2c95c-181">Regras para métodos: Métodos derivados não podem alterar a acessibilidade do método base.</span><span class="sxs-lookup"><span data-stu-id="2c95c-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="2c95c-182">Para o comportamento padrão, todos os métodos derivados que não são anotados são `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="2c95c-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="2c95c-183">Derivados de tipos critical causam uma exceção seja gerada se o método substituído não é anotado explicitamente como `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="2c95c-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="2c95c-184">A tabela a seguir mostra o tipo permitido padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="2c95c-184">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="2c95c-185">Classe base</span><span class="sxs-lookup"><span data-stu-id="2c95c-185">Base class</span></span>|<span data-ttu-id="2c95c-186">Classe derivada pode ser</span><span class="sxs-lookup"><span data-stu-id="2c95c-186">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="2c95c-187">A tabela a seguir mostra o tipo não permitido em padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="2c95c-187">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="2c95c-188">Classe base</span><span class="sxs-lookup"><span data-stu-id="2c95c-188">Base class</span></span>|<span data-ttu-id="2c95c-189">Classe derivada não pode ser</span><span class="sxs-lookup"><span data-stu-id="2c95c-189">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="2c95c-190">A tabela a seguir mostra o método permitido padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="2c95c-190">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="2c95c-191">Método base</span><span class="sxs-lookup"><span data-stu-id="2c95c-191">Base method</span></span>|<span data-ttu-id="2c95c-192">Método derivado pode ser</span><span class="sxs-lookup"><span data-stu-id="2c95c-192">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="2c95c-193">A tabela a seguir mostra o método não permitido em padrões de herança.</span><span class="sxs-lookup"><span data-stu-id="2c95c-193">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="2c95c-194">Método base</span><span class="sxs-lookup"><span data-stu-id="2c95c-194">Base method</span></span>|<span data-ttu-id="2c95c-195">Método derivado não pode ser</span><span class="sxs-lookup"><span data-stu-id="2c95c-195">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="2c95c-196">Essas regras de herança se aplicam a membros e tipos de nível 2.</span><span class="sxs-lookup"><span data-stu-id="2c95c-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="2c95c-197">Tipos em assemblies de nível 1 podem herdar de membros e tipos de segurança crítica de nível 2.</span><span class="sxs-lookup"><span data-stu-id="2c95c-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="2c95c-198">Portanto, os membros e tipos de nível 2 devem ter demandas de herança separados para os herdeiros de nível 1.</span><span class="sxs-lookup"><span data-stu-id="2c95c-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

[<span data-ttu-id="2c95c-199">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="2c95c-199">Back to top</span></span>](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a><span data-ttu-id="2c95c-200">Informações Adicionais e Regras</span><span class="sxs-lookup"><span data-stu-id="2c95c-200">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="2c95c-201">Suporte LinkDemand</span><span class="sxs-lookup"><span data-stu-id="2c95c-201">LinkDemand Support</span></span>

<span data-ttu-id="2c95c-202">O modelo de transparência de nível 2 substitui o <xref:System.Security.Permissions.SecurityAction.LinkDemand> com o <xref:System.Security.SecurityCriticalAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="2c95c-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="2c95c-203">No código herdado (nível 1), uma <xref:System.Security.Permissions.SecurityAction.LinkDemand> são tratados automaticamente como um <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="2c95c-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="2c95c-204">Reflexão</span><span class="sxs-lookup"><span data-stu-id="2c95c-204">Reflection</span></span>

<span data-ttu-id="2c95c-205">Invocar um método crítico ou a leitura de um campo crítica aciona uma demanda para confiança total (como se você invocou um método particular ou campo).</span><span class="sxs-lookup"><span data-stu-id="2c95c-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="2c95c-206">Portanto, o código de confiança total pode invocar um método crítico, enquanto o código de confiança parcial não pode.</span><span class="sxs-lookup"><span data-stu-id="2c95c-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="2c95c-207">As propriedades a seguir foram adicionadas para o <xref:System.Reflection> namespace para determinar se o tipo, método ou campo é `SecurityCritical`, `SecuritySafeCritical`, ou `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="2c95c-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="2c95c-208">Use essas propriedades para determinar a transparência por meio de reflexão em vez de verificar a presença do atributo.</span><span class="sxs-lookup"><span data-stu-id="2c95c-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="2c95c-209">As regras de transparência são complexas e verificando o atributo pode não ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="2c95c-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="2c95c-210">Um `SafeCritical` retorn `true` para ambos <xref:System.Type.IsSecurityCritical%2A> e <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, pois `SafeCritical` é realmente fundamental (ele tem os mesmos recursos que o código critical, mas ele pode ser chamado no código transparent).</span><span class="sxs-lookup"><span data-stu-id="2c95c-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="2c95c-211">Métodos dinâmicos herdam a transparência dos módulos que eles são anexados a; eles não herdam a transparência do tipo (se eles são anexados a um tipo).</span><span class="sxs-lookup"><span data-stu-id="2c95c-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="2c95c-212">Ignorar Verificação em Confiança Total</span><span class="sxs-lookup"><span data-stu-id="2c95c-212">Skip Verification in Full Trust</span></span>

<span data-ttu-id="2c95c-213">Você pode ignorar a verificação de assemblies transparentes totalmente confiáveis, definindo o <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade para `true` no <xref:System.Security.SecurityRulesAttribute> atributo:</span><span class="sxs-lookup"><span data-stu-id="2c95c-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="2c95c-214">O <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> é de propriedade `false` por padrão, portanto, a propriedade deve ser definida como `true` para ignorar a verificação.</span><span class="sxs-lookup"><span data-stu-id="2c95c-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="2c95c-215">Isso deve ser feito para apenas para fins de otimização.</span><span class="sxs-lookup"><span data-stu-id="2c95c-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="2c95c-216">Você deve garantir que o código transparente no assembly é verificável usando o `transparent` opção de [ferramenta PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="2c95c-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c95c-217">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c95c-217">See also</span></span>

- [<span data-ttu-id="2c95c-218">Código transparente de segurança, nível 1</span><span class="sxs-lookup"><span data-stu-id="2c95c-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [<span data-ttu-id="2c95c-219">Alterações de segurança</span><span class="sxs-lookup"><span data-stu-id="2c95c-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
