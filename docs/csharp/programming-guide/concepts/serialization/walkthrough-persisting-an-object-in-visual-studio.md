---
title: 'Passo a passo: Persistindo um objeto usando o C#'
ms.date: 04/26/2018
ms.openlocfilehash: c3cff57f008eb524c2d2bec406431e4c41dca617
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568135"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="a220b-102">Passo a passo: Persistindo um objeto usando o C#</span><span class="sxs-lookup"><span data-stu-id="a220b-102">Walkthrough: persisting an object using C#</span></span> #

<span data-ttu-id="a220b-103">Você pode usar a serialização para manter os dados de um objeto entre instâncias, o que permite armazenar valores e recuperá-los na próxima vez que o objeto for instanciado.</span><span class="sxs-lookup"><span data-stu-id="a220b-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="a220b-104">Neste passo a passo, você criará um objeto `Loan` básico e persistirá seus dados em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a220b-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="a220b-105">Em seguida, você recuperará os dados do arquivo quando recriar o objeto.</span><span class="sxs-lookup"><span data-stu-id="a220b-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a220b-106">Este exemplo criará um novo arquivo se o arquivo ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="a220b-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="a220b-107">Se um aplicativo precisar criar um arquivo, esse aplicativo precisará ter a permissão `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="a220b-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="a220b-108">Permissões são definidas usando listas de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="a220b-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="a220b-109">Se o arquivo já existir, o aplicativo precisará somente da permissão `Write`, que é uma permissão menor.</span><span class="sxs-lookup"><span data-stu-id="a220b-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="a220b-110">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder permissões `Read` a um único arquivo (em vez das permissões Create para uma pasta).</span><span class="sxs-lookup"><span data-stu-id="a220b-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="a220b-111">Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta Arquivos de Programas.</span><span class="sxs-lookup"><span data-stu-id="a220b-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a220b-112">Este exemplo armazena dados em um arquivo de formato binário.</span><span class="sxs-lookup"><span data-stu-id="a220b-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="a220b-113">Esses formatos não devem ser usados para dados confidenciais, como senhas ou informações de cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="a220b-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a220b-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a220b-114">Prerequisites</span></span>

* <span data-ttu-id="a220b-115">Para criar e executar, instale o [SDK do .NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="a220b-115">To build and run, install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="a220b-116">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="a220b-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="a220b-117">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="a220b-117">Need to install a code editor?</span></span> <span data-ttu-id="a220b-118">Experimente o [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="a220b-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

<span data-ttu-id="a220b-119">Examine o código de exemplo online [no repositório GitHub de amostras do .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="a220b-119">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="a220b-120">Criando o objeto Loan</span><span class="sxs-lookup"><span data-stu-id="a220b-120">Creating the loan object</span></span>

<span data-ttu-id="a220b-121">A primeira etapa é criar uma classe `Loan` e um aplicativo de console que usa a classe:</span><span class="sxs-lookup"><span data-stu-id="a220b-121">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="a220b-122">Crie um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a220b-122">Create a new application.</span></span> <span data-ttu-id="a220b-123">Digite `dotnet new console -o serialization` para criar um novo aplicativo de console em um subdiretório chamado `serialization`.</span><span class="sxs-lookup"><span data-stu-id="a220b-123">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="a220b-124">Abra o aplicativo no editor e adicione uma nova classe chamada `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="a220b-124">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="a220b-125">Adicione o seguinte código à classe `Loan`:</span><span class="sxs-lookup"><span data-stu-id="a220b-125">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="a220b-126">Você também precisará criar um aplicativo que usa a classe `Loan`.</span><span class="sxs-lookup"><span data-stu-id="a220b-126">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="a220b-127">Serializar o objeto Loan</span><span class="sxs-lookup"><span data-stu-id="a220b-127">Serialize the loan object</span></span>

1. <span data-ttu-id="a220b-128">Abra `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="a220b-128">Open `Program.cs`.</span></span> <span data-ttu-id="a220b-129">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a220b-129">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="a220b-130">Adicione um manipulador de eventos ao evento `PropertyChanged` e algumas linhas para modificar o objeto `Loan` e exibir as alterações.</span><span class="sxs-lookup"><span data-stu-id="a220b-130">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="a220b-131">Veja as adições no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a220b-131">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="a220b-132">Neste ponto, você pode executar o código e ver a saída atual:</span><span class="sxs-lookup"><span data-stu-id="a220b-132">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="a220b-133">A execução desse aplicativo repetidamente grava os mesmos valores.</span><span class="sxs-lookup"><span data-stu-id="a220b-133">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="a220b-134">Um novo objeto Loan é criado sempre que o programa é executado.</span><span class="sxs-lookup"><span data-stu-id="a220b-134">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="a220b-135">No mundo real, as taxas de juros mudam periodicamente, mas não necessariamente toda vez que o aplicativo for executado.</span><span class="sxs-lookup"><span data-stu-id="a220b-135">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="a220b-136">Código de serialização significa preservar a taxa de juros mais recente entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a220b-136">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="a220b-137">Na próxima etapa, você fará exatamente isso adicionando a serialização à classe Loan.</span><span class="sxs-lookup"><span data-stu-id="a220b-137">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="a220b-138">Usando a serialização para manter o objeto</span><span class="sxs-lookup"><span data-stu-id="a220b-138">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="a220b-139">Para manter os valores da classe Loan, primeiro você deve marcar a classe com o atributo `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="a220b-139">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="a220b-140">Adicione o seguinte código acima da definição da classe Loan:</span><span class="sxs-lookup"><span data-stu-id="a220b-140">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="a220b-141">O <xref:System.SerializableAttribute> informa ao compilador que tudo na classe pode ser persistido em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a220b-141">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="a220b-142">Como o evento `PropertyChanged` não representa a parte do grafo do objeto que deve ser armazenada, ele não deve ser serializado.</span><span class="sxs-lookup"><span data-stu-id="a220b-142">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="a220b-143">Ao fazer isso, todos os objetos anexados a esse evento serão serializados.</span><span class="sxs-lookup"><span data-stu-id="a220b-143">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="a220b-144">Adicione o <xref:System.NonSerializedAttribute> à declaração de campo do manipulador de eventos `PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="a220b-144">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="a220b-145">Do C# 7.3 em diante, você pode anexar atributos ao campo de suporte de uma propriedade autoimplementada usando o valor de destino `field`.</span><span class="sxs-lookup"><span data-stu-id="a220b-145">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="a220b-146">O seguinte código adiciona uma propriedade `TimeLastLoaded` e a marca como não serializável:</span><span class="sxs-lookup"><span data-stu-id="a220b-146">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="a220b-147">A etapa seguinte é adicionar o código de serialização ao aplicativo LoanApp.</span><span class="sxs-lookup"><span data-stu-id="a220b-147">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="a220b-148">Para serializar a classe e gravá-la em um arquivo, use os namespaces <xref:System.IO> e <xref:System.Runtime.Serialization.Formatters.Binary>.</span><span class="sxs-lookup"><span data-stu-id="a220b-148">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="a220b-149">Para evitar a digitação dos nomes totalmente qualificados, você pode adicionar referências aos namespaces necessários, conforme mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a220b-149">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="a220b-150">A próxima etapa é adicionar código para desserializar o objeto do arquivo quando o objeto for criado.</span><span class="sxs-lookup"><span data-stu-id="a220b-150">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="a220b-151">Adicione uma constante à classe do nome de arquivo dos dados serializados, conforme mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a220b-151">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="a220b-152">Em seguida, adicione o seguinte código após a linha que cria o objeto `TestLoan`:</span><span class="sxs-lookup"><span data-stu-id="a220b-152">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="a220b-153">Primeiro, é necessário verificar se o arquivo existe.</span><span class="sxs-lookup"><span data-stu-id="a220b-153">You first must check that the file exists.</span></span> <span data-ttu-id="a220b-154">Se ele existir, crie uma classe <xref:System.IO.Stream> para ler o arquivo binário e uma classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para converter o arquivo.</span><span class="sxs-lookup"><span data-stu-id="a220b-154">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="a220b-155">Você também precisa converter do tipo de fluxo para o tipo de objeto Loan.</span><span class="sxs-lookup"><span data-stu-id="a220b-155">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="a220b-156">Em seguida, é necessário adicionar um código para serializar a classe em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a220b-156">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="a220b-157">Adicione o seguinte código após o código existente no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="a220b-157">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="a220b-158">Neste ponto, você pode compilar e executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="a220b-158">At this point, you can again build and run the application.</span></span> <span data-ttu-id="a220b-159">Na primeira vez em que ele é executado, observe que as taxas de juros começam em 7,5 e, em seguida, são alteradas para 7,1.</span><span class="sxs-lookup"><span data-stu-id="a220b-159">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="a220b-160">Feche o aplicativo e execute-o novamente.</span><span class="sxs-lookup"><span data-stu-id="a220b-160">Close the application and then run it again.</span></span> <span data-ttu-id="a220b-161">Agora, o aplicativo imprime a mensagem indicando que ele leu o arquivo salvo e a taxa de juros é 7,1, mesmo antes do código que a altera.</span><span class="sxs-lookup"><span data-stu-id="a220b-161">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="a220b-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a220b-162">See Also</span></span>

- [<span data-ttu-id="a220b-163">Serialização (C#)</span><span class="sxs-lookup"><span data-stu-id="a220b-163">Serialization (C#)</span></span>](index.md)  
- [<span data-ttu-id="a220b-164">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a220b-164">C# Programming Guide</span></span>](../..//index.md)  
