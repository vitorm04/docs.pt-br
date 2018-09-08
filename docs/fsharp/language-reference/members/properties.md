---
title: Propriedades (F#)
description: 'Saiba mais sobre propriedades F #, que são membros que representam os valores associados a um objeto.'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130400"
---
# <a name="properties"></a><span data-ttu-id="08e0b-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="08e0b-103">Properties</span></span>

<span data-ttu-id="08e0b-104">*Propriedades* são membros que representam os valores associados a um objeto.</span><span class="sxs-lookup"><span data-stu-id="08e0b-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="08e0b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08e0b-105">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="08e0b-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="08e0b-106">Remarks</span></span>

<span data-ttu-id="08e0b-107">Propriedades representam o "tem um" relação na programação orientada a objeto, que representa os dados que está associados com instâncias de objeto ou, para propriedades estáticas, com o tipo.</span><span class="sxs-lookup"><span data-stu-id="08e0b-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="08e0b-108">Você pode declarar propriedades de duas maneiras, dependendo se você deseja especificar explicitamente o valor subjacente (também chamado de repositório de backup) para a propriedade, ou se você deseja permitir que o compilador gerar automaticamente o repositório de backup para você.</span><span class="sxs-lookup"><span data-stu-id="08e0b-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="08e0b-109">Em geral, você deve usar a maneira mais explícita, se a propriedade tem uma implementação não triviais e forma automática quando a propriedade é apenas um wrapper simples para um valor ou uma variável.</span><span class="sxs-lookup"><span data-stu-id="08e0b-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="08e0b-110">Para declarar uma propriedade explicitamente, use o `member` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="08e0b-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="08e0b-111">Essa sintaxe declarativa é seguido pela sintaxe que especifica o `get` e `set` métodos, também denominados *acessadores*.</span><span class="sxs-lookup"><span data-stu-id="08e0b-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="08e0b-112">As várias formas da sintaxe explícita mostrado na seção de sintaxe são usadas para propriedades de leitura/gravação, somente leitura e somente gravação.</span><span class="sxs-lookup"><span data-stu-id="08e0b-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="08e0b-113">Para propriedades somente leitura, você define apenas um `get` método; para propriedades somente gravação, defina apenas um `set` método.</span><span class="sxs-lookup"><span data-stu-id="08e0b-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="08e0b-114">Observe que, quando uma propriedade tiver tanto `get` e `set` acessadores, a sintaxe alternativa permite que você especifique atributos e modificadores de acessibilidade que são diferentes para cada acessador, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="08e0b-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="08e0b-115">Para propriedades de leitura/gravação, que têm ambas uma `get` e `set` método, a ordem dos `get` e `set` pode ser revertida.</span><span class="sxs-lookup"><span data-stu-id="08e0b-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="08e0b-116">Como alternativa, você pode fornecer a sintaxe mostrada para `get` apenas e a sintaxe mostrada para `set` somente, em vez de usar a sintaxe combinada.</span><span class="sxs-lookup"><span data-stu-id="08e0b-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="08e0b-117">Isso torna mais fácil para comentar o indivíduo `get` ou `set` método, se isso é algo que talvez você precise fazer.</span><span class="sxs-lookup"><span data-stu-id="08e0b-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="08e0b-118">Essa alternativa usando a sintaxe combinada é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="08e0b-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="08e0b-119">Privada valores que espera que os dados para as propriedades são chamados *repositório de backup*.</span><span class="sxs-lookup"><span data-stu-id="08e0b-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="08e0b-120">Para fazer com que o compilador criar automaticamente o repositório de backup, use as palavras-chave `member val`, omitir o identificador de Self e, em seguida, forneça uma expressão para inicializar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="08e0b-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="08e0b-121">Se a propriedade deve ser mutáveis, incluir `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="08e0b-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="08e0b-122">Por exemplo, o seguinte tipo de classe inclui duas propriedades implementadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="08e0b-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="08e0b-123">`Property1` é somente leitura e é inicializada para o argumento fornecido para o construtor primário, e `Property2` é uma propriedade configurável, inicializada como uma cadeia de caracteres vazia:</span><span class="sxs-lookup"><span data-stu-id="08e0b-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="08e0b-124">Propriedades implementadas automaticamente fazem parte da inicialização de um tipo, portanto, eles devem ser incluídos antes das outras definições de membro, assim como `let` associações e `do` ligações em uma definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="08e0b-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="08e0b-125">Observe que a expressão que inicializa uma propriedade implementada automaticamente é avaliada apenas na inicialização e não sempre que a propriedade é acessada.</span><span class="sxs-lookup"><span data-stu-id="08e0b-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="08e0b-126">Esse comportamento é diferente do comportamento de uma propriedade implementada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="08e0b-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="08e0b-127">Isso efetivamente significa que o código para inicializar essas propriedades é adicionado ao construtor de uma classe.</span><span class="sxs-lookup"><span data-stu-id="08e0b-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="08e0b-128">Considere o seguinte código que mostra essa diferença:</span><span class="sxs-lookup"><span data-stu-id="08e0b-128">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

<span data-ttu-id="08e0b-129">**Saída**</span><span class="sxs-lookup"><span data-stu-id="08e0b-129">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="08e0b-130">A saída do código anterior mostra que o valor de AutoProperty é inalterado quando chamado várias vezes, enquanto o ExplicitProperty muda sempre que ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="08e0b-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="08e0b-131">Isso demonstra que a expressão para uma propriedade implementada automaticamente não é avaliada a cada vez, pois é o método de getter da propriedade explícita.</span><span class="sxs-lookup"><span data-stu-id="08e0b-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
<span data-ttu-id="08e0b-132">Há algumas bibliotecas, como o Entity Framework (`System.Data.Entity`) que executam operações personalizadas em construtores de classe base que não funcionam bem com a inicialização de propriedades implementadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="08e0b-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="08e0b-133">Nesses casos, tente usar propriedades explícitas.</span><span class="sxs-lookup"><span data-stu-id="08e0b-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="08e0b-134">Propriedades podem ser membros de classes, estruturas, uniões discriminadas, registros, interfaces e extensões de tipo e também podem ser definidas em expressões de objeto.</span><span class="sxs-lookup"><span data-stu-id="08e0b-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="08e0b-135">Atributos podem ser aplicados às propriedades.</span><span class="sxs-lookup"><span data-stu-id="08e0b-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="08e0b-136">Para aplicar um atributo a uma propriedade, gravar o atributo em uma linha separada antes da propriedade.</span><span class="sxs-lookup"><span data-stu-id="08e0b-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="08e0b-137">Para obter mais informações, consulte [Atributos](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="08e0b-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="08e0b-138">Por padrão, as propriedades são públicas.</span><span class="sxs-lookup"><span data-stu-id="08e0b-138">By default, properties are public.</span></span> <span data-ttu-id="08e0b-139">Modificadores de acessibilidade também podem ser aplicados a propriedades.</span><span class="sxs-lookup"><span data-stu-id="08e0b-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="08e0b-140">Para aplicar um modificador de acessibilidade, adicioná-lo imediatamente antes do nome da propriedade caso ele deva ser aplicado a ambas as `get` e `set` métodos; adicioná-lo antes do `get` e `set` palavras-chave se for de acessibilidade diferente necessário para cada acessador.</span><span class="sxs-lookup"><span data-stu-id="08e0b-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="08e0b-141">O *modificador de acessibilidade* pode ser uma das seguintes opções: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="08e0b-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="08e0b-142">Para saber mais, veja [Controle de acesso](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="08e0b-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="08e0b-143">Implementações de propriedade são executadas sempre que uma propriedade é acessada.</span><span class="sxs-lookup"><span data-stu-id="08e0b-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="08e0b-144">Estáticos e propriedades da instância</span><span class="sxs-lookup"><span data-stu-id="08e0b-144">Static and Instance Properties</span></span>

<span data-ttu-id="08e0b-145">As propriedades podem ser estáticos ou propriedades da instância.</span><span class="sxs-lookup"><span data-stu-id="08e0b-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="08e0b-146">Propriedades podem ser chamadas sem uma instância e estáticos são usadas para valores associados com o tipo, não com objetos individuais.</span><span class="sxs-lookup"><span data-stu-id="08e0b-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="08e0b-147">Para propriedades estáticas, omita o identificador de Self.</span><span class="sxs-lookup"><span data-stu-id="08e0b-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="08e0b-148">O identificador de Self é necessário para as propriedades de instância.</span><span class="sxs-lookup"><span data-stu-id="08e0b-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="08e0b-149">A seguinte definição de propriedade estática é baseada em um cenário em que você tenha um campo estático `myStaticValue` que é o repositório de backup para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="08e0b-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="08e0b-150">As propriedades também podem ser de tipo de matriz, nesse caso, eles são chamados *propriedades indexadas*.</span><span class="sxs-lookup"><span data-stu-id="08e0b-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="08e0b-151">Para obter mais informações, consulte [as propriedades indexadas](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="08e0b-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="08e0b-152">Anotação de tipo para propriedades</span><span class="sxs-lookup"><span data-stu-id="08e0b-152">Type Annotation for Properties</span></span>

<span data-ttu-id="08e0b-153">Em muitos casos, o compilador tem informações suficientes para inferir o tipo de uma propriedade do tipo de repositório de backup, mas você pode definir o tipo explicitamente adicionando uma anotação de tipo.</span><span class="sxs-lookup"><span data-stu-id="08e0b-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="08e0b-154">Usando a propriedade definir acessadores</span><span class="sxs-lookup"><span data-stu-id="08e0b-154">Using Property set Accessors</span></span>

<span data-ttu-id="08e0b-155">Você pode definir propriedades que fornecem `set` acessadores usando o `<-` operador.</span><span class="sxs-lookup"><span data-stu-id="08e0b-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="08e0b-156">A saída é **20**.</span><span class="sxs-lookup"><span data-stu-id="08e0b-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="08e0b-157">Propriedades abstratas</span><span class="sxs-lookup"><span data-stu-id="08e0b-157">Abstract Properties</span></span>

<span data-ttu-id="08e0b-158">As propriedades podem ser abstratas.</span><span class="sxs-lookup"><span data-stu-id="08e0b-158">Properties can be abstract.</span></span> <span data-ttu-id="08e0b-159">Assim como acontece com métodos, `abstract` apenas significa que há uma expedição virtual associada à propriedade.</span><span class="sxs-lookup"><span data-stu-id="08e0b-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="08e0b-160">Propriedades abstratas podem ser realmente abstratas, ou seja, sem uma definição na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="08e0b-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="08e0b-161">Portanto, a classe que contém essa propriedade é uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="08e0b-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="08e0b-162">Como alternativa, abstrata apenas pode significar que uma propriedade é virtual e, nesse caso, uma definição deve estar presente na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="08e0b-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="08e0b-163">Observe que propriedades abstratas não devem ser particulares e, se um acessador é abstrato, o outro também deverá ser abstrato.</span><span class="sxs-lookup"><span data-stu-id="08e0b-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="08e0b-164">Para obter mais informações sobre classes abstratas, consulte [Classes abstratas](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="08e0b-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="08e0b-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08e0b-165">See also</span></span>

- [<span data-ttu-id="08e0b-166">Membros</span><span class="sxs-lookup"><span data-stu-id="08e0b-166">Members</span></span>](index.md)
- [<span data-ttu-id="08e0b-167">Métodos</span><span class="sxs-lookup"><span data-stu-id="08e0b-167">Methods</span></span>](methods.md)
