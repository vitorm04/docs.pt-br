---
title: Aplicando atributos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e23649c5d833bef8b74ec5d3b9c22235756580e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="applying-attributes"></a><span data-ttu-id="91cc0-102">Aplicando atributos</span><span class="sxs-lookup"><span data-stu-id="91cc0-102">Applying Attributes</span></span>
<span data-ttu-id="91cc0-103">Use o processo a seguir para aplicar um atributo a um elemento do seu código.</span><span class="sxs-lookup"><span data-stu-id="91cc0-103">Use the following process to apply an attribute to an element of your code.</span></span>  
  
1.  <span data-ttu-id="91cc0-104">Definir um novo atributo ou use um atributo existente importando seu namespace do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91cc0-104">Define a new attribute or use an existing attribute by importing its namespace from the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="91cc0-105">Aplique o atributo para o elemento de código, colocando-o imediatamente antes do elemento.</span><span class="sxs-lookup"><span data-stu-id="91cc0-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>  
  
     <span data-ttu-id="91cc0-106">Cada linguagem tem sua própria sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="91cc0-107">Em C++ e c#, o atributo é circundado por colchetes e separado do elemento por espaço em branco, que pode incluir uma quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="91cc0-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="91cc0-108">No Visual Basic, o atributo é delimitado por colchetes angulares e deve estar na mesma linha lógica; o caractere de continuação de linha pode ser usado se uma quebra de linha é desejada.</span><span class="sxs-lookup"><span data-stu-id="91cc0-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>
  
3.  <span data-ttu-id="91cc0-109">Especifique parâmetros posicionais e parâmetros nomeados para o atributo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-109">Specify positional parameters and named parameters for the attribute.</span></span>  
  
     <span data-ttu-id="91cc0-110">Parâmetros posicionais são necessários e devem vir antes de quaisquer parâmetros nomeados; eles correspondem aos parâmetros de um dos construtores do atributo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-110">Positional parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="91cc0-111">Parâmetros nomeados são opcionais e correspondem às propriedades do atributo de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="91cc0-111">Named parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="91cc0-112">Em C++ e c#, especifique `name` = `value` para cada parâmetro opcional, onde `name` é o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="91cc0-112">In C++, and C#, specify `name`=`value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="91cc0-113">No Visual Basic, especifique `name`: =`value`.</span><span class="sxs-lookup"><span data-stu-id="91cc0-113">In Visual Basic, specify `name`:=`value`.</span></span>  
  
 <span data-ttu-id="91cc0-114">O atributo é emitido em metadados quando você compila o código e está disponível para o common language runtime e qualquer ferramenta personalizada ou um aplicativo por meio dos serviços de reflexão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91cc0-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>  
  
 <span data-ttu-id="91cc0-115">Por convenção, todos os nomes de atributo terminam com atributo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-115">By convention, all attribute names end with Attribute.</span></span> <span data-ttu-id="91cc0-116">No entanto, várias linguagens que direcionam o tempo de execução, como Visual Basic e c#, não exigem que você especifique o nome completo de um atributo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="91cc0-117">Por exemplo, se você deseja inicializar <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, você só precisa fazer referência a ele como **obsoleto**.</span><span class="sxs-lookup"><span data-stu-id="91cc0-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>  
  
## <a name="applying-an-attribute-to-a-method"></a><span data-ttu-id="91cc0-118">Aplicar um atributo a um método</span><span class="sxs-lookup"><span data-stu-id="91cc0-118">Applying an Attribute to a Method</span></span>  
 <span data-ttu-id="91cc0-119">O exemplo de código a seguir mostra como declarar **System. ObsoleteAttribute**, que as marcas de código como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="91cc0-119">The following code example shows how to declare **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="91cc0-120">A cadeia de caracteres `"Will be removed in next version"` é passado para o atributo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="91cc0-121">Esse atributo faz com que um aviso do compilador que exibe a cadeia de caracteres transmitida ao código que descreve o atributo é chamado.</span><span class="sxs-lookup"><span data-stu-id="91cc0-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a><span data-ttu-id="91cc0-122">Aplicando atributos no nível de Assembly</span><span class="sxs-lookup"><span data-stu-id="91cc0-122">Applying Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="91cc0-123">Se você quiser aplicar um atributo no nível de assembly, use o **assembly** (`Assembly` no Visual Basic) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="91cc0-123">If you want to apply an attribute at the assembly level, use the **assembly** (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="91cc0-124">O código a seguir mostra o **AssemblyTitleAttribute** aplicada no nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="91cc0-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 <span data-ttu-id="91cc0-125">Quando esse atributo é aplicado, a cadeia de caracteres `"My Assembly"` é colocado no manifesto do assembly na parte de metadados do arquivo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="91cc0-126">Você pode exibir o atributo usando o [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou criando um programa personalizado para recuperar o atributo.</span><span class="sxs-lookup"><span data-stu-id="91cc0-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91cc0-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91cc0-127">See Also</span></span>  
 [<span data-ttu-id="91cc0-128">Atributos</span><span class="sxs-lookup"><span data-stu-id="91cc0-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="91cc0-129">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="91cc0-129">Retrieving Information Stored in Attributes</span></span>](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="91cc0-130">Conceitos</span><span class="sxs-lookup"><span data-stu-id="91cc0-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)  
 [<span data-ttu-id="91cc0-131">Atributos</span><span class="sxs-lookup"><span data-stu-id="91cc0-131">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
