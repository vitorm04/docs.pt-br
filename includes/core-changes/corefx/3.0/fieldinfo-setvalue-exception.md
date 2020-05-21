---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721328"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="2572a-101">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="2572a-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="2572a-102">A partir do .NET Core 3,0, uma exceção é lançada quando você tenta definir um valor em um campo estático, <xref:System.Reflection.FieldAttributes.InitOnly> chamando <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="2572a-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2572a-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="2572a-103">Change description</span></span>

<span data-ttu-id="2572a-104">Em .NET Framework e versões do .NET Core anteriores a 3,0, você pode definir o valor de um campo estático que é constante depois que ele é inicializado ([ReadOnly em C#](~/docs/csharp/language-reference/keywords/readonly.md)) chamando <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="2572a-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="2572a-105">No entanto, a definição desse campo dessa forma resultou em um comportamento imprevisível com base na estrutura de destino e nas configurações de otimização.</span><span class="sxs-lookup"><span data-stu-id="2572a-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="2572a-106">No .NET Core 3,0 e versões posteriores, quando você chama <xref:System.Reflection.FieldInfo.SetValue%2A> em um campo estático, <xref:System.Reflection.FieldAttributes.InitOnly> uma <xref:System.FieldAccessException?displayProperty=nameWithType> exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="2572a-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="2572a-107">Um <xref:System.Reflection.FieldAttributes.InitOnly> campo é aquele que só pode ser definido no momento em que é declarado ou no construtor para a classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="2572a-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="2572a-108">Em outras palavras, é constante depois que ela é inicializada.</span><span class="sxs-lookup"><span data-stu-id="2572a-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2572a-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2572a-109">Version introduced</span></span>

<span data-ttu-id="2572a-110">3.0</span><span class="sxs-lookup"><span data-stu-id="2572a-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2572a-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2572a-111">Recommended action</span></span>

<span data-ttu-id="2572a-112">Inicialize os campos estáticos <xref:System.Reflection.FieldAttributes.InitOnly> em um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="2572a-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="2572a-113">Isso se aplica a tipos dinâmicos e não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="2572a-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="2572a-114">Como alternativa, você pode remover o <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atributo do campo e, em seguida, chamar <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2572a-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="2572a-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="2572a-115">Category</span></span>

<span data-ttu-id="2572a-116">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="2572a-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2572a-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2572a-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
