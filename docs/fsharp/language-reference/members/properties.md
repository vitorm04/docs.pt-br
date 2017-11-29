---
title: Propriedades (F#)
description: "Saiba mais sobre F # propriedades, que são membros que representam os valores associados a um objeto."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a><span data-ttu-id="7432f-104">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7432f-104">Properties</span></span>

<span data-ttu-id="7432f-105">*Propriedades* membros que representam os valores associados a um objeto.</span><span class="sxs-lookup"><span data-stu-id="7432f-105">*Properties* are members that represent values associated with an object.</span></span>


## <a name="syntax"></a><span data-ttu-id="7432f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7432f-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="7432f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7432f-107">Remarks</span></span>
<span data-ttu-id="7432f-108">Representa propriedades de "tem um" relação em programação orientada a objeto, que representa os dados associados com instâncias de objeto ou, para propriedades estáticas, com o tipo.</span><span class="sxs-lookup"><span data-stu-id="7432f-108">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="7432f-109">Você pode declarar propriedades de duas maneiras, dependendo se você deseja especificar explicitamente o valor subjacente (também chamado de armazenamento de backup) para a propriedade, ou se você deseja permitir que o compilador gerar automaticamente o repositório de backup para você.</span><span class="sxs-lookup"><span data-stu-id="7432f-109">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="7432f-110">Em geral, você deve usar a forma mais explícita se a propriedade tem uma implementação não trivial e o modo automático quando a propriedade é apenas um wrapper simple para um valor ou uma variável.</span><span class="sxs-lookup"><span data-stu-id="7432f-110">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="7432f-111">Para declarar explicitamente uma propriedade, use o `member` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="7432f-111">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="7432f-112">Essa sintaxe declarativa é seguido pela sintaxe que especifica o `get` e `set` métodos, também denominados *acessadores*.</span><span class="sxs-lookup"><span data-stu-id="7432f-112">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="7432f-113">As várias formas da sintaxe explícita mostrado na seção de sintaxe são usadas para propriedades somente leitura e gravação de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="7432f-113">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="7432f-114">Propriedades somente leitura, você define apenas um `get` método; propriedades somente gravação, defina apenas um `set` método.</span><span class="sxs-lookup"><span data-stu-id="7432f-114">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="7432f-115">Observe que, quando uma propriedade com ambos `get` e `set` acessadores, a sintaxe alternativa permite que você especifique atributos e os modificadores de acessibilidade que são diferentes para cada acessador, conforme é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7432f-115">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="7432f-116">Para propriedades de leitura/gravação, que têm ambos um `get` e `set` método, a ordem de `get` e `set` podem ser revertidas.</span><span class="sxs-lookup"><span data-stu-id="7432f-116">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="7432f-117">Como alternativa, você pode fornecer a sintaxe mostrada para `get` apenas e a sintaxe mostrada para `set` somente, em vez de usar a sintaxe combinada.</span><span class="sxs-lookup"><span data-stu-id="7432f-117">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="7432f-118">Isso torna mais fácil para comentar o indivíduo `get` ou `set` método, se isso é algo que você pode precisar fazer.</span><span class="sxs-lookup"><span data-stu-id="7432f-118">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="7432f-119">Essa alternativa usando a sintaxe combinada é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7432f-119">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="7432f-120">Privada que espera que os dados para as propriedades são chamados de valores *armazenamentos de backup*.</span><span class="sxs-lookup"><span data-stu-id="7432f-120">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="7432f-121">Para fazer com que o compilador cria automaticamente o repositório de backup, use as palavras-chave `member val`, omita o identificador interno e forneça uma expressão para inicializar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="7432f-121">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="7432f-122">Se a propriedade é ser mutável, incluir `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="7432f-122">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="7432f-123">Por exemplo, o seguinte tipo de classe inclui duas propriedades implementadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7432f-123">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="7432f-124">`Property1`é somente leitura e é inicializado para o argumento fornecido para o construtor primário, e `Property2` é uma propriedade definível inicializada para uma cadeia de caracteres vazia:</span><span class="sxs-lookup"><span data-stu-id="7432f-124">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="7432f-125">Propriedades implementadas automaticamente fazem parte da inicialização de um tipo, elas devem ser incluídas antes de quaisquer outras definições de membro, como `let` associações e `do` associações em uma definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="7432f-125">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="7432f-126">Observe que a expressão que inicializa uma propriedade implementada automaticamente é avaliada apenas na inicialização e não toda vez que a propriedade for acessada.</span><span class="sxs-lookup"><span data-stu-id="7432f-126">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="7432f-127">Esse comportamento é diferente do comportamento de uma propriedade implementada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="7432f-127">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="7432f-128">O que isso significa é que o código para inicializar a essas propriedades é adicionado ao construtor de uma classe.</span><span class="sxs-lookup"><span data-stu-id="7432f-128">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="7432f-129">Considere o seguinte código que mostra essa diferença:</span><span class="sxs-lookup"><span data-stu-id="7432f-129">Consider the following code that shows this difference:</span></span>

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

<span data-ttu-id="7432f-130">**Saída**</span><span class="sxs-lookup"><span data-stu-id="7432f-130">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="7432f-131">A saída do código anterior mostra que o valor de AutoProperty é alterado quando chamado repetidamente, enquanto o ExplicitProperty mudará sempre que ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="7432f-131">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="7432f-132">Isso demonstra que a expressão para uma propriedade implementada automaticamente não é avaliada toda vez que é o método de getter da propriedade explícita.</span><span class="sxs-lookup"><span data-stu-id="7432f-132">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>


>[!WARNING]
<span data-ttu-id="7432f-133">Há algumas bibliotecas, como o Entity Framework (`System.Data.Entity`) que executam operações personalizadas em construtores de classe base que não funcionam bem com a inicialização de propriedades implementadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7432f-133">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="7432f-134">Nesses casos, tente usar propriedades explícitas.</span><span class="sxs-lookup"><span data-stu-id="7432f-134">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="7432f-135">Propriedades podem ser membros de classes, estruturas, uniões discriminadas, registros, interfaces e extensões de tipo e também podem ser definidas em expressões de objeto.</span><span class="sxs-lookup"><span data-stu-id="7432f-135">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="7432f-136">Atributos podem ser aplicados às propriedades.</span><span class="sxs-lookup"><span data-stu-id="7432f-136">Attributes can be applied to properties.</span></span> <span data-ttu-id="7432f-137">Para aplicar um atributo a uma propriedade, grave o atributo em uma linha separada antes da propriedade.</span><span class="sxs-lookup"><span data-stu-id="7432f-137">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="7432f-138">Para obter mais informações, consulte [Atributos](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7432f-138">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="7432f-139">Por padrão, as propriedades são públicas.</span><span class="sxs-lookup"><span data-stu-id="7432f-139">By default, properties are public.</span></span> <span data-ttu-id="7432f-140">Modificadores de acessibilidade também podem ser aplicadas às propriedades.</span><span class="sxs-lookup"><span data-stu-id="7432f-140">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="7432f-141">Para aplicar um modificador de acessibilidade, adicione-o imediatamente antes do nome da propriedade se ele deve se aplicam a ambos os `get` e `set` métodos; adicioná-lo antes do `get` e `set` palavras-chave se acessibilidade diferente é necessário para cada acessador.</span><span class="sxs-lookup"><span data-stu-id="7432f-141">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="7432f-142">O *modificador de acessibilidade* pode ser um dos seguintes: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="7432f-142">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="7432f-143">Para saber mais, veja [Controle de acesso](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="7432f-143">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="7432f-144">Implementações de propriedade são executadas sempre que uma propriedade é acessada.</span><span class="sxs-lookup"><span data-stu-id="7432f-144">Property implementations are executed each time a property is accessed.</span></span>


## <a name="static-and-instance-properties"></a><span data-ttu-id="7432f-145">Estático e propriedades da instância</span><span class="sxs-lookup"><span data-stu-id="7432f-145">Static and Instance Properties</span></span>
<span data-ttu-id="7432f-146">Propriedades podem ser estáticos ou propriedades da instância.</span><span class="sxs-lookup"><span data-stu-id="7432f-146">Properties can be static or instance properties.</span></span> <span data-ttu-id="7432f-147">Propriedades estáticas podem ser chamadas sem uma instância e são usadas para valores associados com o tipo, não com objetos individuais.</span><span class="sxs-lookup"><span data-stu-id="7432f-147">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="7432f-148">Para propriedades estáticas, omita o identificador interno.</span><span class="sxs-lookup"><span data-stu-id="7432f-148">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="7432f-149">O identificador interno é necessário para as propriedades de instância.</span><span class="sxs-lookup"><span data-stu-id="7432f-149">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="7432f-150">A seguinte definição de propriedade estática baseia-se em um cenário em que você tenha um campo estático `myStaticValue` que é o repositório de backup para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="7432f-150">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="7432f-151">Propriedades também podem ser tipo de matriz, caso em que eles são chamados *propriedades indexadas*.</span><span class="sxs-lookup"><span data-stu-id="7432f-151">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="7432f-152">Para obter mais informações, consulte [propriedades indexadas](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="7432f-152">For more information, see [Indexed Properties](indexed-properties.md).</span></span>


## <a name="type-annotation-for-properties"></a><span data-ttu-id="7432f-153">Anotação de tipo para propriedades</span><span class="sxs-lookup"><span data-stu-id="7432f-153">Type Annotation for Properties</span></span>
<span data-ttu-id="7432f-154">Em muitos casos, o compilador não tem informações suficientes para inferir o tipo de uma propriedade do tipo de armazenamento de backup, mas você pode definir o tipo explicitamente adicionando uma anotação de tipo.</span><span class="sxs-lookup"><span data-stu-id="7432f-154">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="7432f-155">Usando a propriedade acessadores definidos</span><span class="sxs-lookup"><span data-stu-id="7432f-155">Using Property set Accessors</span></span>
<span data-ttu-id="7432f-156">Você pode definir propriedades que fornecem `set` acessadores usando o `<-` operador.</span><span class="sxs-lookup"><span data-stu-id="7432f-156">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="7432f-157">A saída é **20**.</span><span class="sxs-lookup"><span data-stu-id="7432f-157">The output is **20**.</span></span>


## <a name="abstract-properties"></a><span data-ttu-id="7432f-158">Propriedades abstratas</span><span class="sxs-lookup"><span data-stu-id="7432f-158">Abstract Properties</span></span>
<span data-ttu-id="7432f-159">Propriedades podem ser abstratas.</span><span class="sxs-lookup"><span data-stu-id="7432f-159">Properties can be abstract.</span></span> <span data-ttu-id="7432f-160">Como com métodos, `abstract` apenas significa que há um despacho virtual associado à propriedade.</span><span class="sxs-lookup"><span data-stu-id="7432f-160">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="7432f-161">Propriedades abstratas podem ser realmente abstratas, ou seja, sem uma definição na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="7432f-161">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="7432f-162">A classe que contém essa propriedade, portanto, é uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="7432f-162">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="7432f-163">Como alternativa, abstrato apenas pode significar que uma propriedade é virtual e, nesse caso, uma definição deve estar presente na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="7432f-163">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="7432f-164">Observe que propriedades abstratas não devem ser privadas, e se um acessador é abstrato, o outro também deverá ser abstrato.</span><span class="sxs-lookup"><span data-stu-id="7432f-164">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="7432f-165">Para obter mais informações sobre classes abstratas, consulte [Classes abstratas](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7432f-165">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="7432f-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7432f-166">See Also</span></span>
[<span data-ttu-id="7432f-167">Membros</span><span class="sxs-lookup"><span data-stu-id="7432f-167">Members</span></span>](index.md)

[<span data-ttu-id="7432f-168">Métodos</span><span class="sxs-lookup"><span data-stu-id="7432f-168">Methods</span></span>](methods.md)
