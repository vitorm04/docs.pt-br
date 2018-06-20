---
title: 'Arquivos de assinatura (F #)'
description: 'Saiba como usar arquivos de assinatura de F # para manter informações sobre as assinaturas públicas de um conjunto de F # elementos do programa, como módulos, tipos e namespaces.'
ms.date: 06/15/2018
ms.openlocfilehash: 21e1b1d1cb67ea64206070a947d667fd52441dd8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208659"
---
# <a name="signatures"></a><span data-ttu-id="f2609-103">Assinaturas</span><span class="sxs-lookup"><span data-stu-id="f2609-103">Signatures</span></span>

<span data-ttu-id="f2609-104">Um arquivo de assinatura contém informações sobre as assinaturas públicas de um conjunto de elementos de programação de F#, como tipos, namespaces e módulos.</span><span class="sxs-lookup"><span data-stu-id="f2609-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="f2609-105">Ele pode ser usado para especificar a acessibilidade desses elementos de programa.</span><span class="sxs-lookup"><span data-stu-id="f2609-105">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="f2609-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2609-106">Remarks</span></span>
<span data-ttu-id="f2609-107">Para cada arquivo de código F #, você pode ter um *arquivo de assinatura*, que é um arquivo que tem o mesmo nome que o arquivo de código, mas com o. FSI de extensão em vez de. FS.</span><span class="sxs-lookup"><span data-stu-id="f2609-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="f2609-108">Arquivos de assinatura também podem ser adicionados à compilação de linha de comando se você estiver usando a linha de comando diretamente.</span><span class="sxs-lookup"><span data-stu-id="f2609-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="f2609-109">Para fazer a distinção entre arquivos de código e arquivos de assinatura, arquivos de código são às vezes chamados de *arquivos de implementação*.</span><span class="sxs-lookup"><span data-stu-id="f2609-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="f2609-110">Em um projeto, o arquivo de assinatura deve preceder o arquivo de código associado.</span><span class="sxs-lookup"><span data-stu-id="f2609-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="f2609-111">Um arquivo de assinatura descreve os namespaces, módulos, tipos e membros no arquivo de implementação correspondente.</span><span class="sxs-lookup"><span data-stu-id="f2609-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="f2609-112">Use as informações em um arquivo de assinatura para especificar quais partes do código na implementação correspondente de arquivo pode ser acessado pelo código fora do arquivo de implementação e quais partes são internos para o arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="f2609-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="f2609-113">Os namespaces, módulos e tipos que são incluídos no arquivo de assinatura devem ser um subconjunto dos namespaces, módulos e tipos que são incluídos no arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="f2609-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="f2609-114">Com algumas exceções indicadas neste tópico, os elementos de linguagem que não estão listados no arquivo de assinatura são considerados particulares para o arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="f2609-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="f2609-115">Se nenhum arquivo de assinatura for encontrado no projeto ou na linha de comando, a acessibilidade padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="f2609-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="f2609-116">Para obter mais informações sobre a acessibilidade padrão, consulte [controle de acesso](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="f2609-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="f2609-117">Em um arquivo de assinatura, você não se repetem a definição dos tipos e as implementações de cada método ou função.</span><span class="sxs-lookup"><span data-stu-id="f2609-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="f2609-118">Em vez disso, use a assinatura para cada método e a função, que atua como uma especificação completa da funcionalidade que é implementada por um fragmento de namespace ou módulo.</span><span class="sxs-lookup"><span data-stu-id="f2609-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="f2609-119">A sintaxe para uma assinatura de tipo é a mesma usada em declarações de método abstract em interfaces e classes abstratas e também é mostrada a IntelliSense e o fsi.exe interpretador F # quando ele for exibido entrada compilada corretamente.</span><span class="sxs-lookup"><span data-stu-id="f2609-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="f2609-120">Se não há informações suficientes na assinatura de tipo para indicar se um tipo é lacrado, ou se é um tipo de interface, você deve adicionar um atributo que indica a natureza do tipo para o compilador.</span><span class="sxs-lookup"><span data-stu-id="f2609-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="f2609-121">Atributos que você pode usar para essa finalidade são descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2609-121">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="f2609-122">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2609-122">Attribute</span></span>|<span data-ttu-id="f2609-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2609-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="f2609-124">Para um tipo que não tem nenhum membro abstrato ou que não deve ser estendido.</span><span class="sxs-lookup"><span data-stu-id="f2609-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="f2609-125">Para um tipo que é uma interface.</span><span class="sxs-lookup"><span data-stu-id="f2609-125">For a type that is an interface.</span></span>|
<span data-ttu-id="f2609-126">O compilador gera um erro se os atributos não são consistentes entre a assinatura e a declaração no arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="f2609-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="f2609-127">Use a palavra-chave `val` para criar uma assinatura para um valor ou o valor da função.</span><span class="sxs-lookup"><span data-stu-id="f2609-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="f2609-128">A palavra-chave `type` apresenta uma assinatura de tipo.</span><span class="sxs-lookup"><span data-stu-id="f2609-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="f2609-129">Você pode gerar um arquivo de assinatura usando o `--sig` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="f2609-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="f2609-130">Em geral, você não gravar arquivos. FSI manualmente.</span><span class="sxs-lookup"><span data-stu-id="f2609-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="f2609-131">Em vez disso, você gerar arquivos. FSI, usando o compilador, adicioná-los ao seu projeto, se você tiver um e editá-los, removendo os métodos e as funções que você não deseja ser acessível.</span><span class="sxs-lookup"><span data-stu-id="f2609-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="f2609-132">Há várias regras para assinaturas de tipo:</span><span class="sxs-lookup"><span data-stu-id="f2609-132">There are several rules for type signatures:</span></span>


- <span data-ttu-id="f2609-133">Abreviações de tipo em um arquivo de implementação não devem corresponder a um tipo sem uma abreviação em um arquivo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="f2609-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="f2609-134">Registros e uniões discriminadas devem expor todos ou nenhum de seus campos e construtores, e a ordem em que a assinatura deve corresponder à ordem em que o arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="f2609-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="f2609-135">Classes podem revelar alguns, todos ou nenhum de seus campos e métodos na assinatura.</span><span class="sxs-lookup"><span data-stu-id="f2609-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="f2609-136">Classes e estruturas que tenham construtores devem expor as declarações de suas classes base (o `inherits` declaração).</span><span class="sxs-lookup"><span data-stu-id="f2609-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="f2609-137">Além disso, classes e estruturas que tenham construtores devem expor todos os métodos abstratos e declarações de interface.</span><span class="sxs-lookup"><span data-stu-id="f2609-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="f2609-138">Tipos de interface devem revelar todos os seus métodos e interfaces.</span><span class="sxs-lookup"><span data-stu-id="f2609-138">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="f2609-139">As regras para assinaturas de valor são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f2609-139">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="f2609-140">Modificadores de acessibilidade (`public`, `internal`, e assim por diante) e o `inline` e `mutable` modificadores na assinatura devem corresponder na implementação.</span><span class="sxs-lookup"><span data-stu-id="f2609-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="f2609-141">O número de parâmetros de tipo genérico (ou inferido implicitamente ou explicitamente declarado) deve corresponder e os tipos e as restrições de tipo em parâmetros de tipo genérico devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="f2609-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="f2609-142">Se o `Literal` atributo é usado, ele deverá aparecer na assinatura e a implementação e o mesmo valor literal deve ser usado para ambos.</span><span class="sxs-lookup"><span data-stu-id="f2609-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="f2609-143">O padrão de parâmetros (também conhecido como o *arity*) de assinaturas e implementações devem ser consistentes.</span><span class="sxs-lookup"><span data-stu-id="f2609-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


- <span data-ttu-id="f2609-144">Se forem diferentes nomes de parâmetro em um arquivo de assinatura do arquivo de implementação correspondente, o nome no arquivo de assinatura será usado em vez disso, que pode causar problemas quando a depuração ou a criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="f2609-144">If parameter names in a signature file differ from the corresponding implementation file, the name in the signature file will be used instead, which may cause issues when debugging or profiling.</span></span> <span data-ttu-id="f2609-145">Se você deseja ser notificado de tais incompatibilidades, habilitar aviso 3218 no arquivo de projeto ou ao invocar o compilador (consulte `--warnon` em [opções do compilador](compiler-options.md)).</span><span class="sxs-lookup"><span data-stu-id="f2609-145">If you wish to be notified of such mismatches, enable warning 3218 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](compiler-options.md)).</span></span>


<span data-ttu-id="f2609-146">O exemplo de código a seguir mostra um exemplo de um arquivo de assinatura que tem o namespace, módulo, valor da função e as assinaturas de tipo junto com os atributos apropriados.</span><span class="sxs-lookup"><span data-stu-id="f2609-146">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="f2609-147">Ele também mostra o arquivo de implementação correspondente.</span><span class="sxs-lookup"><span data-stu-id="f2609-147">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="f2609-148">O código a seguir mostra o arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="f2609-148">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="f2609-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2609-149">See Also</span></span>
[<span data-ttu-id="f2609-150">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="f2609-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f2609-151">Controle de Acesso</span><span class="sxs-lookup"><span data-stu-id="f2609-151">Access Control</span></span>](access-control.md)

[<span data-ttu-id="f2609-152">Opções do Compilador</span><span class="sxs-lookup"><span data-stu-id="f2609-152">Compiler Options</span></span>](compiler-options.md)
