---
title: "Criando threads e passando dados na hora de início"
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
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="666c8-102">Criando threads e passando dados na hora de início</span><span class="sxs-lookup"><span data-stu-id="666c8-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="666c8-103">Quando um processo do sistema operacional é criado, o sistema operacional injeta um thread para executar o código no processo, incluindo qualquer domínio de aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="666c8-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="666c8-104">Desse ponto em diante, os domínios de aplicativo podem ser criados e destruídos sem qualquer threads do sistema operacional necessariamente que está sendo criado ou destruído.</span><span class="sxs-lookup"><span data-stu-id="666c8-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="666c8-105">Se o código que está sendo executado é gerenciado código, em seguida, um <xref:System.Threading.Thread> do objeto para o thread em execução no domínio do aplicativo atual pode ser obtida recuperando estático <xref:System.Threading.Thread.CurrentThread%2A> propriedade do tipo <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="666c8-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="666c8-106">Este tópico descreve a criação de thread e aborda alternativas para passar dados para o procedimento de thread.</span><span class="sxs-lookup"><span data-stu-id="666c8-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="666c8-107">Criar um Thread</span><span class="sxs-lookup"><span data-stu-id="666c8-107">Creating a Thread</span></span>  
 <span data-ttu-id="666c8-108">Criando um novo <xref:System.Threading.Thread> objeto cria um novo thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="666c8-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="666c8-109">O <xref:System.Threading.Thread> classe tem construtores que usam um <xref:System.Threading.ThreadStart> delegar ou um <xref:System.Threading.ParameterizedThreadStart> delegar; o representante encapsula o método é invocado por novo thread quando você chamar o <xref:System.Threading.Thread.Start%2A> método.</span><span class="sxs-lookup"><span data-stu-id="666c8-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="666c8-110">Chamando <xref:System.Threading.Thread.Start%2A> mais de uma vez, faz com que um <xref:System.Threading.ThreadStateException> seja gerada.</span><span class="sxs-lookup"><span data-stu-id="666c8-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="666c8-111">O <xref:System.Threading.Thread.Start%2A> método retorna imediatamente, muitas vezes antes do novo segmento realmente foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="666c8-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="666c8-112">Você pode usar o <xref:System.Threading.Thread.ThreadState%2A> e <xref:System.Threading.Thread.IsAlive%2A> propriedades para determinar o estado do thread em um dado momento, mas essas propriedades nunca devem ser usado para sincronizar as atividades de threads.</span><span class="sxs-lookup"><span data-stu-id="666c8-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="666c8-113">Depois que um thread é iniciado, não é necessário manter uma referência para o <xref:System.Threading.Thread> objeto.</span><span class="sxs-lookup"><span data-stu-id="666c8-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="666c8-114">O thread continua a executar até que o procedimento de thread termina.</span><span class="sxs-lookup"><span data-stu-id="666c8-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="666c8-115">O exemplo de código a seguir cria dois novos threads para chamar a instância e métodos estáticos em outro objeto.</span><span class="sxs-lookup"><span data-stu-id="666c8-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="666c8-116">Transmitindo dados para Threads e recuperando dados de Threads</span><span class="sxs-lookup"><span data-stu-id="666c8-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="666c8-117">No .NET Framework versão 2.0, o <xref:System.Threading.ParameterizedThreadStart> representante fornece uma maneira fácil para passar um objeto que contém dados a um thread quando você chama o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> sobrecarga do método.</span><span class="sxs-lookup"><span data-stu-id="666c8-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="666c8-118">Consulte <xref:System.Threading.ParameterizedThreadStart> para obter um exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="666c8-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="666c8-119">Usando o <xref:System.Threading.ParameterizedThreadStart> delegado não é uma maneira de tipo seguro para passar dados, porque o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> sobrecarga do método aceita qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="666c8-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="666c8-120">Uma alternativa é encapsular o procedimento de thread e os dados em uma classe auxiliar e usar o <xref:System.Threading.ThreadStart> representante para executar o procedimento de thread.</span><span class="sxs-lookup"><span data-stu-id="666c8-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="666c8-121">Essa técnica é mostrada nos dois exemplos de código que segue.</span><span class="sxs-lookup"><span data-stu-id="666c8-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="666c8-122">Nenhum deles delegados tem um valor de retorno, porque não há nenhum local para retornar os dados de uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="666c8-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="666c8-123">Para recuperar os resultados de um método de thread, você pode usar um método de retorno de chamada, conforme demonstrado no segundo exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="666c8-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="666c8-124">Recuperação de dados com os métodos de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="666c8-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="666c8-125">O exemplo a seguir demonstra um método de retorno de chamada que recupera dados de um thread.</span><span class="sxs-lookup"><span data-stu-id="666c8-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="666c8-126">O construtor para a classe que contém os dados e o método de thread também aceita um delegado que representa o método de retorno de chamada; antes do método de thread termina, ele chama o representante de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="666c8-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="666c8-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="666c8-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="666c8-128">Threading</span><span class="sxs-lookup"><span data-stu-id="666c8-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="666c8-129">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="666c8-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
