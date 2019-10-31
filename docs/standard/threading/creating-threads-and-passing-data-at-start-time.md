---
title: Criando threads e passando dados na hora de início
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: a628cbb4c9ec8e1c9ccd9fd73e72a82ecf2b2836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138099"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="5b9eb-102">Criando threads e passando dados na hora de início</span><span class="sxs-lookup"><span data-stu-id="5b9eb-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="5b9eb-103">Quando um processo do sistema operacional é criado, o sistema operacional injeta um thread para executar o código nesse processo, incluindo qualquer domínio de aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="5b9eb-104">Desse ponto em diante, os domínios de aplicativo podem ser criados e destruídos sem qualquer criação ou destruição de threads do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="5b9eb-105">Se o código que estiver sendo executado for um código gerenciado, um objeto <xref:System.Threading.Thread> para o thread em execução no domínio do aplicativo atual poderá ser obtido recuperando a propriedade <xref:System.Threading.Thread.CurrentThread%2A> estática do tipo <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="5b9eb-106">Este tópico descreve a criação de thread e aborda alternativas para passar dados para o procedimento do thread.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="5b9eb-107">Criação de um thread</span><span class="sxs-lookup"><span data-stu-id="5b9eb-107">Creating a thread</span></span>

 <span data-ttu-id="5b9eb-108">A criação de um novo objeto <xref:System.Threading.Thread> cria um novo thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="5b9eb-109">A classe <xref:System.Threading.Thread> tem construtores que usam um delegado <xref:System.Threading.ThreadStart> ou um delegado <xref:System.Threading.ParameterizedThreadStart>; o delegado encapsula o método invocado pelo novo thread quando você chama o método <xref:System.Threading.Thread.Start%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="5b9eb-110">Chamar <xref:System.Threading.Thread.Start%2A> mais de uma vez faz com que uma <xref:System.Threading.ThreadStateException> seja lançada.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="5b9eb-111">O método <xref:System.Threading.Thread.Start%2A> retorna imediatamente, muitas vezes antes do novo thread realmente começar.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="5b9eb-112">Você pode usar as propriedades <xref:System.Threading.Thread.ThreadState%2A> e <xref:System.Threading.Thread.IsAlive%2A> para determinar o estado do thread a qualquer momento, mas essas propriedades nunca devem ser usadas para sincronizar as atividades dos threads.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b9eb-113">Após o início do thread, não é necessário manter uma referência ao objeto <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="5b9eb-114">O thread continua a executar até que o procedimento do thread termine.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="5b9eb-115">O exemplo de código a seguir cria dois novos threads para chamar métodos de instância e estáticos em outro objeto.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="5b9eb-116">Passando dados para threads</span><span class="sxs-lookup"><span data-stu-id="5b9eb-116">Passing data to threads</span></span>

 <span data-ttu-id="5b9eb-117">No .NET Framework versão 2.0, o delegado <xref:System.Threading.ParameterizedThreadStart> fornece uma maneira fácil para passar um objeto que contém dados para um thread quando você chama a sobrecarga do método <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="5b9eb-118">Consulte <xref:System.Threading.ParameterizedThreadStart> para obter um exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="5b9eb-119">Usar o delegado <xref:System.Threading.ParameterizedThreadStart> não é uma maneira fortemente tipada de passar dados, pois a sobrecarga do método <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> aceita qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="5b9eb-120">Uma alternativa é encapsular o procedimento do thread e os dados em uma classe auxiliar e usar o delegado <xref:System.Threading.ThreadStart> para executar o procedimento de thread.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="5b9eb-121">O exemplo a seguir demonstra essa técnica:</span><span class="sxs-lookup"><span data-stu-id="5b9eb-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="5b9eb-122">Nenhum dos delegados <xref:System.Threading.ThreadStart> e <xref:System.Threading.ParameterizedThreadStart> tem um valor retornado, porque não há um local para retornar os dados de uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="5b9eb-123">Para recuperar os resultados de um método de thread, é possível usar um método de retorno de chamada, conforme mostrado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="5b9eb-124">Recuperação de dados de threads com métodos de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="5b9eb-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="5b9eb-125">O exemplo a seguir demonstra um método de retorno de chamada que recupera dados de um thread.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="5b9eb-126">O construtor para a classe que contém os dados e o método de thread também aceita um delegado que representa o método de retorno de chamada; antes do método de thread terminar, ele invoca o delegado de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="5b9eb-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5b9eb-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b9eb-127">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5b9eb-128">Threading</span><span class="sxs-lookup"><span data-stu-id="5b9eb-128">Threading</span></span>](index.md)
- [<span data-ttu-id="5b9eb-129">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="5b9eb-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
