---
title: Aplicando atributos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 24fe58ddf48e40b422652baa4c5bba86eea6b84f
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889225"
---
# <a name="apply-attributes"></a><span data-ttu-id="c8bdb-102">Aplicar atributos</span><span class="sxs-lookup"><span data-stu-id="c8bdb-102">Apply attributes</span></span>

<span data-ttu-id="c8bdb-103">Use o processo a seguir para aplicar um atributo a um elemento do código.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-103">Use the following process to apply an attribute to an element of your code.</span></span>

1. <span data-ttu-id="c8bdb-104">Defina um novo atributo ou use um atributo existente do .NET.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-104">Define a new attribute or use an existing .NET attribute.</span></span>

2. <span data-ttu-id="c8bdb-105">Aplique o atributo ao elemento de código, colocando-o imediatamente antes do elemento.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>

     <span data-ttu-id="c8bdb-106">Cada linguagem tem sua própria sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="c8bdb-107">Em C++ e C#, o atributo é delimitado por colchetes e separado do elemento por um espaço em branco, que pode incluir uma quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="c8bdb-108">No Visual Basic, o atributo é delimitado por colchetes angulares e deve estar na mesma linha lógica. O caractere de continuação de linha pode ser usado se você quiser uma quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>

3. <span data-ttu-id="c8bdb-109">Especifique parâmetros posicionais e parâmetros nomeados para o atributo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-109">Specify positional parameters and named parameters for the attribute.</span></span>

     <span data-ttu-id="c8bdb-110">Os parâmetros *posicionais* são obrigatórios e devem vir antes de quaisquer parâmetros nomeados; Elas correspondem aos parâmetros de um dos construtores do atributo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-110">*Positional* parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="c8bdb-111">Os parâmetros *nomeados* são opcionais e correspondem às propriedades de leitura/gravação do atributo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-111">*Named* parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="c8bdb-112">Em C++ e C#, especifique `name=value` para cada parâmetro opcional, em que `name` é o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-112">In C++, and C#, specify `name=value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="c8bdb-113">Em Visual Basic, especifique `name:=value` .</span><span class="sxs-lookup"><span data-stu-id="c8bdb-113">In Visual Basic, specify `name:=value`.</span></span>

 <span data-ttu-id="c8bdb-114">O atributo é emitido em metadados quando você compila o código e está disponível para o Common Language Runtime e todas as ferramentas ou aplicativos personalizados por meio dos serviços de reflexão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>

 <span data-ttu-id="c8bdb-115">Por convenção, todos os nomes de atributo terminam com "Attribute".</span><span class="sxs-lookup"><span data-stu-id="c8bdb-115">By convention, all attribute names end with "Attribute".</span></span> <span data-ttu-id="c8bdb-116">No entanto, várias linguagens que têm como destino o runtime, como Visual Basic e C#, não exigem que você especifique o nome completo de um atributo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="c8bdb-117">Por exemplo, se quiser inicializar <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, você só precisa fazer referência a ele como **Obsoleto** .</span><span class="sxs-lookup"><span data-stu-id="c8bdb-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete** .</span></span>

## <a name="apply-an-attribute-to-a-method"></a><span data-ttu-id="c8bdb-118">Aplicar um atributo a um método</span><span class="sxs-lookup"><span data-stu-id="c8bdb-118">Apply an attribute to a method</span></span>

 <span data-ttu-id="c8bdb-119">O exemplo de código a seguir mostra como usar **System. ObsoleteAttribute** , que marca o código como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-119">The following code example shows how to use **System.ObsoleteAttribute** , which marks code as obsolete.</span></span> <span data-ttu-id="c8bdb-120">A cadeia de caracteres `"Will be removed in next version"` é passada para o atributo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="c8bdb-121">Esse atributo faz com que o compilador que exibe a cadeia de caracteres transmitida emita um aviso quando o código que descreve o atributo for chamado.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a><span data-ttu-id="c8bdb-122">Aplicar atributos no nível do assembly</span><span class="sxs-lookup"><span data-stu-id="c8bdb-122">Apply attributes at the assembly level</span></span>

 <span data-ttu-id="c8bdb-123">Se você quiser aplicar um atributo no nível do assembly, use a `assembly` `Assembly` palavra-chave (no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c8bdb-123">If you want to apply an attribute at the assembly level, use the `assembly` (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="c8bdb-124">O código a seguir mostra o **AssemblyTitleAttribute** aplicado no nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 <span data-ttu-id="c8bdb-125">Quando esse atributo é aplicado, a cadeia de caracteres `"My Assembly"` é colocada no manifesto do assembly na parte de metadados do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="c8bdb-126">Você pode exibir o atributo usando o [Desmontador de MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) ou criando um programa personalizado para recuperar o atributo.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8bdb-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="c8bdb-127">See also</span></span>

- [<span data-ttu-id="c8bdb-128">Atributos</span><span class="sxs-lookup"><span data-stu-id="c8bdb-128">Attributes</span></span>](index.md)
- [<span data-ttu-id="c8bdb-129">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="c8bdb-129">Retrieving Information Stored in Attributes</span></span>](retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="c8bdb-130">Conceitos</span><span class="sxs-lookup"><span data-stu-id="c8bdb-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="c8bdb-131">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="c8bdb-131">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="c8bdb-132">Visão geral de atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8bdb-132">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
