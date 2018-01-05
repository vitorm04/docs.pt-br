---
title: "Exemplo de tecnologia de serialização básica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3d269b7603c63db73fdcbab91b777e69b228cc9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="6abcc-102">Exemplo de tecnologia de serialização básica</span><span class="sxs-lookup"><span data-stu-id="6abcc-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="6abcc-103">Baixar exemplo</span><span class="sxs-lookup"><span data-stu-id="6abcc-103">Download sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="6abcc-104">Esse exemplo demonstra a habilidade do common language runtime de serializar um grafo de objeto na memória para um fluxo.</span><span class="sxs-lookup"><span data-stu-id="6abcc-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="6abcc-105">Esse exemplo pode usar o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ou o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para serialização.</span><span class="sxs-lookup"><span data-stu-id="6abcc-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="6abcc-106">Uma lista vinculada, preenchida com dados, é serializada ou desserializada para ou de um fluxo de arquivos.</span><span class="sxs-lookup"><span data-stu-id="6abcc-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="6abcc-107">Em ambos os casos, a lista é exibida para que você possa ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="6abcc-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="6abcc-108">A lista vinculada é do tipo `LinkedList`, um tipo definido por essa amostra.</span><span class="sxs-lookup"><span data-stu-id="6abcc-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="6abcc-109">Revise os comentários no código de origem e nos arquivos build.proj para obter mais informações sobre serialização.</span><span class="sxs-lookup"><span data-stu-id="6abcc-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="6abcc-110">Para criar o exemplo usando o Prompt de Comando</span><span class="sxs-lookup"><span data-stu-id="6abcc-110">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="6abcc-111">Navegue para um dos subdiretórios específicos da linguagem no diretório Technologies\Serialization\Runtime Serialization\Basic directory, usando o prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="6abcc-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="6abcc-112">Digite **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** ou **msbuild SerializationVB.sln**, dependendo de sua escolha da linguagem de programação, na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6abcc-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="6abcc-113">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6abcc-113">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="6abcc-114">Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para um dos subdiretórios específicos da linguagem para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="6abcc-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="6abcc-115">Clique duas vezes no ícone para o arquivo SerializationCS.sln, SerializationJSL.sln ou SerializationVB.sln, dependendo de sua escolha da linguagem de programação para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6abcc-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="6abcc-116">No menu **Compilar**, selecione **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="6abcc-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="6abcc-117">O aplicativo de exemplo será criado no subdiretório padrão \bin ou \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="6abcc-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="6abcc-118">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="6abcc-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="6abcc-119">Navegue para o diretório contendo o executável compilado.</span><span class="sxs-lookup"><span data-stu-id="6abcc-119">Navigate to the directory containing the built executable.</span></span>  
  
2.  <span data-ttu-id="6abcc-120">Digite **Serialization.exe**, junto com os valores de parâmetro desejados, na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6abcc-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6abcc-121">Esse exemplo cria um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="6abcc-121">This sample builds a console application.</span></span> <span data-ttu-id="6abcc-122">Você deve lançá-lo usando o prompt de comando para exibir a saída.</span><span class="sxs-lookup"><span data-stu-id="6abcc-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6abcc-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="6abcc-123">Remarks</span></span>  
 <span data-ttu-id="6abcc-124">O aplicativo de exemplo aceita parâmetros da linha de comando indicando qual teste você gostaria de executar.</span><span class="sxs-lookup"><span data-stu-id="6abcc-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="6abcc-125">Para serializar uma lista de 10 nós para um arquivo chamado **Test.xml** usando o formatador SOAP, use os parâmetros **sx Test.xml 10**.</span><span class="sxs-lookup"><span data-stu-id="6abcc-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="6abcc-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6abcc-126">For Example:</span></span>  
  
 <span data-ttu-id="6abcc-127">**Serialize.exe -sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="6abcc-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="6abcc-128">Para desserializar o arquivo **Test.xml** do exemplo anterior, use os parâmetros **dx Test.xml**.</span><span class="sxs-lookup"><span data-stu-id="6abcc-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="6abcc-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6abcc-129">For Example:</span></span>  
  
 <span data-ttu-id="6abcc-130">**Serialize.exe -dx Test.xml**</span><span class="sxs-lookup"><span data-stu-id="6abcc-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="6abcc-131">Nos dois exemplos acima, o "x" na opção de linha de comando indica que você quer a serialização SOAP de XML.</span><span class="sxs-lookup"><span data-stu-id="6abcc-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="6abcc-132">Você pode usar "b" nesse local para usar a serialização binária.</span><span class="sxs-lookup"><span data-stu-id="6abcc-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="6abcc-133">Se você quiser tentar a serialização com um número muito grande de nós, pode querer redirecionar a saída do console para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6abcc-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="6abcc-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6abcc-134">For Example:</span></span>  
  
 <span data-ttu-id="6abcc-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span><span class="sxs-lookup"><span data-stu-id="6abcc-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="6abcc-136">Os seguintes marcadores descrevem brevemente as classes e as tecnologias usadas por esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="6abcc-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
-   <span data-ttu-id="6abcc-137">Serialização em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6abcc-137">Runtime Serialization</span></span>  
  
    -   <span data-ttu-id="6abcc-138"><xref:System.Runtime.Serialization.IFormatter> Usado para referir-se a um objeto <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="6abcc-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    -   <span data-ttu-id="6abcc-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Usado para serializar uma lista vinculada a um fluxo em um formato binário.</span><span class="sxs-lookup"><span data-stu-id="6abcc-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="6abcc-140">O formatador binário usa um formato que somente o tipo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> entende.</span><span class="sxs-lookup"><span data-stu-id="6abcc-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="6abcc-141">No entanto, os dados são concisos.</span><span class="sxs-lookup"><span data-stu-id="6abcc-141">However, the data is concise.</span></span>  
  
    -   <span data-ttu-id="6abcc-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Usado para serializar uma lista vinculada a um fluxo no formato SOAP.</span><span class="sxs-lookup"><span data-stu-id="6abcc-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="6abcc-143">SOAP é um formato padrão.</span><span class="sxs-lookup"><span data-stu-id="6abcc-143">SOAP is a standard format.</span></span>  
  
-   <span data-ttu-id="6abcc-144">E/S de fluxo</span><span class="sxs-lookup"><span data-stu-id="6abcc-144">Stream I/O</span></span>  
  
    -   <span data-ttu-id="6abcc-145"><xref:System.IO.Stream> Usado para serializar e desserializar.</span><span class="sxs-lookup"><span data-stu-id="6abcc-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="6abcc-146">O tipo de fluxo específico usado nesse exemplo é o tipo <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="6abcc-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="6abcc-147">No entanto, a serialização pode ser usada com qualquer tipo derivado de <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="6abcc-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    -   <span data-ttu-id="6abcc-148"><xref:System.IO.File> Usado para criar objetos <xref:System.IO.FileStream> para ler e criar arquivos em disco.</span><span class="sxs-lookup"><span data-stu-id="6abcc-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    -   <span data-ttu-id="6abcc-149"><xref:System.IO.FileStream> Usado para serializar e desserializar listas vinculadas.</span><span class="sxs-lookup"><span data-stu-id="6abcc-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6abcc-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6abcc-150">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.Stream>  
 <xref:System.Random>  
 <xref:System.Runtime.Serialization>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.IFormatter>  
 <xref:System.SerializableAttribute>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="6abcc-151">Serialização básica</span><span class="sxs-lookup"><span data-stu-id="6abcc-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="6abcc-152">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="6abcc-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="6abcc-153">Controlando a serialização XML usando atributos</span><span class="sxs-lookup"><span data-stu-id="6abcc-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="6abcc-154">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="6abcc-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="6abcc-155">Serialização</span><span class="sxs-lookup"><span data-stu-id="6abcc-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="6abcc-156">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="6abcc-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
