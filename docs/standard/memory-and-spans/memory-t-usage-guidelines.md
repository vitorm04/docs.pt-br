---
title: Diretrizes de uso de Memory<T> e Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380c0eef137eb5142c30e63f5446f5d60723087a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834053"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="81806-102">Diretrizes de uso de Memory\<T> e Span\<T></span><span class="sxs-lookup"><span data-stu-id="81806-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="81806-103">O .NET Core inclui vários tipos que representam uma região contígua arbitrária de memória.</span><span class="sxs-lookup"><span data-stu-id="81806-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="81806-104">O .NET Core 2.0 introduziu <xref:System.Span%601> e <xref:System.ReadOnlySpan%601>, que são buffers de memória leves que podem ter suporte de memória gerenciada ou não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="81806-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="81806-105">Como esses tipos podem ser armazenados na pilha, eles são inadequados para vários cenários, inclusive chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="81806-105">Because these types can be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="81806-106">O .NET Core 2.1 adiciona vários outros tipos, inclusive <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601> e <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="81806-107">Assim como <xref:System.Span%601>, <xref:System.Memory%601> e os tipos relacionados podem ter suporte de memória gerenciada e não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="81806-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="81806-108">Diferentemente de <xref:System.Span%601>, <xref:System.Memory%601> pode ser armazenado apenas no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="81806-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can only be stored on the managed heap.</span></span>

<span data-ttu-id="81806-109">Tanto <xref:System.Span%601> como <xref:System.Memory%601> representam buffers de dados estruturados que podem ser usados em pipelines.</span><span class="sxs-lookup"><span data-stu-id="81806-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="81806-110">Ou seja, eles são projetados para que alguns ou todos os dados possam ser passados com eficiência para os componentes no pipeline que pode processá-los e, opcionalmente, modificar o buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="81806-111">Como <xref:System.Memory%601> e os tipos relacionados podem ser acessados por vários componentes ou threads, é importante que os desenvolvedores sigam algumas diretrizes de uso padrão para criar um código robusto.</span><span class="sxs-lookup"><span data-stu-id="81806-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="81806-112">Gerenciamento de proprietários, consumidores e vida útil</span><span class="sxs-lookup"><span data-stu-id="81806-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="81806-113">Como os buffers podem ser passados entre APIs e, às vezes, ser acessados de vários threads, é importante levar em consideração o gerenciamento da vida útil.</span><span class="sxs-lookup"><span data-stu-id="81806-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="81806-114">Os três principais conceitos são:</span><span class="sxs-lookup"><span data-stu-id="81806-114">There are three core concepts:</span></span>

- <span data-ttu-id="81806-115">**Propriedade**.</span><span class="sxs-lookup"><span data-stu-id="81806-115">**Ownership**.</span></span> <span data-ttu-id="81806-116">O proprietário de uma instância de buffer é responsável pelo gerenciamento da vida útil, inclusive pela destruição do buffer quando ele não está mais em uso.</span><span class="sxs-lookup"><span data-stu-id="81806-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="81806-117">Todos os buffers pertencem a um único proprietário.</span><span class="sxs-lookup"><span data-stu-id="81806-117">All buffers have a single owner.</span></span> <span data-ttu-id="81806-118">Geralmente, o proprietário é o componente que criou o buffer ou que recebeu o buffer de fábrica.</span><span class="sxs-lookup"><span data-stu-id="81806-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="81806-119">É possível também transferir a propriedade. O **Componente-A** poderá ceder o controle do buffer ao **Componente-B**, passando o **Componente-A** a não poder mais usar o buffer. A partir daí, o **Componente-B** se tornará responsável por destruir o buffer quando ele não estiver mais em uso.</span><span class="sxs-lookup"><span data-stu-id="81806-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="81806-120">**Consumo**.</span><span class="sxs-lookup"><span data-stu-id="81806-120">**Consumption**.</span></span> <span data-ttu-id="81806-121">O consumidor de uma instância do buffer pode usar essa instância, lendo e possivelmente gravando nela.</span><span class="sxs-lookup"><span data-stu-id="81806-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="81806-122">Os buffers podem ter um consumidor por vez, a menos que algum mecanismo de sincronização externo seja fornecido.</span><span class="sxs-lookup"><span data-stu-id="81806-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="81806-123">O consumidor ativo de um buffer não é necessariamente o proprietário do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="81806-124">**Concessão**.</span><span class="sxs-lookup"><span data-stu-id="81806-124">**Lease**.</span></span> <span data-ttu-id="81806-125">A concessão é o período de tempo em que um componente específico pode ser o consumidor do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="81806-126">O exemplo de pseudocódigo a seguir ilustra esses três conceitos.</span><span class="sxs-lookup"><span data-stu-id="81806-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="81806-127">Ele inclui um método `Main` que cria uma instância para o buffer <xref:System.Memory%601> de tipo <xref:System.Char>, chama o método `WriteInt32ToBuffer` para gravar a representação da cadeia de caracteres de um número inteiro no buffer e, em seguida, chama o método `DisplayBufferToConsole` para exibir o valor do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

<span data-ttu-id="81806-128">O método `Main` cria o buffer (neste caso, uma instância de <xref:System.Span%601>), portanto, ele é o respectivo proprietário.</span><span class="sxs-lookup"><span data-stu-id="81806-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="81806-129">Dessa forma, `Main` é responsável por destruir o buffer quando ele não está mais em uso.</span><span class="sxs-lookup"><span data-stu-id="81806-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="81806-130">Ele faz isso chamando o método <xref:System.Span%601.Clear?displayProperty=nameWithType> do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="81806-131">O método <xref:System.Span%601.Clear> realmente limpa a memória do buffer. A estrutura de <xref:System.Span%601> não tem um método que destrua o buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="81806-132">O buffer tem dois consumidores: `WriteInt32ToBuffer` e `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="81806-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="81806-133">Há apenas um consumidor por vez (primeiro `WriteInt32ToBuffer`, depois `DisplayBufferToConsole`), e nenhum dos consumidores é proprietário do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="81806-134">Ainda, "consumidor" neste contexto não implica uma exibição somente leitura do buffer. Os consumidores podem modificar o conteúdo do buffer, assim como `WriteInt32ToBuffer` o faz, se for fornecida uma exibição de leitura/gravação do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="81806-135">O método `WriteInt32ToBuffer` tem uma concessão (pode consumir) o buffer entre o início da chamada do método e a hora em que o método é retornado.</span><span class="sxs-lookup"><span data-stu-id="81806-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="81806-136">Da mesma maneira, `DisplayBufferToConsole` tem uma concessão no buffer enquanto ele está em execução, e a concessão é liberada quando o método é desenrolado.</span><span class="sxs-lookup"><span data-stu-id="81806-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="81806-137">Não há APIs para gerenciamento de concessão. Uma "concessão" é uma questão conceitual.</span><span class="sxs-lookup"><span data-stu-id="81806-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="81806-138">Memory\<T> e o modelo proprietário/consumidor</span><span class="sxs-lookup"><span data-stu-id="81806-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="81806-139">Conforme a seção [Gerenciamento de proprietários, consumidores e vida útil](#owners-consumers-and-lifetime-management) descreve, um buffer tem sempre um proprietário.</span><span class="sxs-lookup"><span data-stu-id="81806-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="81806-140">O .NET Core tem suporte para dois modelos de propriedade:</span><span class="sxs-lookup"><span data-stu-id="81806-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="81806-141">Um modelo com suporte para propriedade única.</span><span class="sxs-lookup"><span data-stu-id="81806-141">A model that supports single ownership.</span></span> <span data-ttu-id="81806-142">Um buffer tem um único proprietário por toda a vida útil.</span><span class="sxs-lookup"><span data-stu-id="81806-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="81806-143">Um modelo com suporte para transferência de propriedade.</span><span class="sxs-lookup"><span data-stu-id="81806-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="81806-144">É possível transferir a propriedade de um buffer do proprietário original (o respectivo criador) para outro componente que se torna responsável pelo gerenciamento da vida útil do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="81806-145">Esse proprietário pode, por sua vez, transferir a propriedade para outro componente, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="81806-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="81806-146">Use a interface <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> para gerenciar explicitamente a propriedade de um buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="81806-147"><xref:System.Buffers.IMemoryOwner%601> tem suporte para os dois modelos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="81806-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="81806-148">O componente que possui uma referência de <xref:System.Buffers.IMemoryOwner%601> possui o buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="81806-149">O exemplo a seguir usa uma instância de <xref:System.Buffers.IMemoryOwner%601?> para refletir a propriedade de um buffer de <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="81806-150">Podemos também escrever este exemplo com [`using`](~/docs/csharp/language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="81806-150">We can also write this example with the [`using`](~/docs/csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="81806-151">Neste código:</span><span class="sxs-lookup"><span data-stu-id="81806-151">In this code:</span></span>

- <span data-ttu-id="81806-152">O método `Main` contém a referência à instância de <xref:System.Buffers.IMemoryOwner%601>, portanto, o método `Main` é o proprietário do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="81806-153">Os métodos `WriteInt32ToBuffer` e `DisplayBufferToConsole` aceitam <xref:System.Memory%601> como uma API pública.</span><span class="sxs-lookup"><span data-stu-id="81806-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="81806-154">Portanto, eles são consumidores do buffer,</span><span class="sxs-lookup"><span data-stu-id="81806-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="81806-155">e o consomem somente um de cada vez.</span><span class="sxs-lookup"><span data-stu-id="81806-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="81806-156">Embora o método `WriteInt32ToBuffer` seja destinado a gravar um valor no buffer, isso não se aplica ao método `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="81806-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="81806-157">Para refletir isso, ele poderia aceitar um argumento de tipo <xref:System.ReadOnlyMemory%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="81806-158">Para saber mais sobre <xref:System.ReadOnlyMemory%601>, confira a [Regra 2: usar ReadOnlySpan\<T> ou ReadOnlyMemory\<T>, se o buffer for somente leitura](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="81806-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="81806-159">Instâncias de Memory\<T> "sem proprietário"</span><span class="sxs-lookup"><span data-stu-id="81806-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="81806-160">É possível criar uma instância de <xref:System.Memory%601> sem usar <xref:System.Buffers.IMemoryOwner%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="81806-161">Nesse caso, a propriedade do buffer é implícita, em vez de explícita, e tem suporte apenas para o modelo de proprietário único.</span><span class="sxs-lookup"><span data-stu-id="81806-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="81806-162">É possível fazer isso da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="81806-162">You can do this by:</span></span>

- <span data-ttu-id="81806-163">Chamar um dos construtores de <xref:System.Memory%601> diretamente, passando um `T[]`, assim como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="81806-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="81806-164">Chamar o método de extensão [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) para criar uma instância de `ReadOnlyMemory<char>`.</span><span class="sxs-lookup"><span data-stu-id="81806-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="81806-165">O método que inicialmente cria a instância de <xref:System.Memory%601> é o proprietário implícito do buffer.</span><span class="sxs-lookup"><span data-stu-id="81806-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="81806-166">Não é possível transferir a propriedade para nenhum outro componente porque não há instâncias de <xref:System.Buffers.IMemoryOwner%601> para facilitar a transferência.</span><span class="sxs-lookup"><span data-stu-id="81806-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="81806-167">Como alternativa, imagine que o coletor de lixo do tempo de execução possui o buffer, e que todos os métodos apenas o consomem.</span><span class="sxs-lookup"><span data-stu-id="81806-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="81806-168">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="81806-168">Usage guidelines</span></span>

<span data-ttu-id="81806-169">Como um bloco de memória pertence, mas se destina a ser passado para vários componentes, alguns dos quais podem operar em um determinado bloco de memória simultaneamente, é importante estabelecer diretrizes para o uso de <xref:System.Memory%601> e <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="81806-170">Diretrizes são necessárias porque:</span><span class="sxs-lookup"><span data-stu-id="81806-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="81806-171">É possível que um componente retenha uma referência a um bloco de memória depois que o respectivo proprietário o liberar.</span><span class="sxs-lookup"><span data-stu-id="81806-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="81806-172">É possível que um componente opere em um buffer, ao mesmo tempo em que outro componente esteja operando nele, corrompendo os dados no buffer durante o processo.</span><span class="sxs-lookup"><span data-stu-id="81806-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="81806-173">Embora a natureza alocada na pilha do <xref:System.Span%601> otimize o desempenho e torne <xref:System.Span%601> o tipo preferencial para a operação em um bloco de memória, ele também submete <xref:System.Span%601> para algumas restrições importantes.</span><span class="sxs-lookup"><span data-stu-id="81806-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="81806-174">É importante saber quando usar <xref:System.Span%601> e quando usar <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="81806-175">A seguir estão nossas recomendações para usar com êxito o <xref:System.Memory%601> e os tipos relacionados.</span><span class="sxs-lookup"><span data-stu-id="81806-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="81806-176">A orientação que se aplica a <xref:System.Memory%601> e a <xref:System.Span%601> também se aplica a <xref:System.ReadOnlyMemory%601> e a <xref:System.ReadOnlySpan%601>, a menos que seja explicitamente definido de outra forma.</span><span class="sxs-lookup"><span data-stu-id="81806-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="81806-177">**Regra 1: no caso de uma API síncrona, usar Span\<T> em vez de Memory\<T> como parâmetro, sempre que possível.**</span><span class="sxs-lookup"><span data-stu-id="81806-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="81806-178"><xref:System.Span%601> é mais versátil do que <xref:System.Memory%601> e pode representar uma variedade maior de buffers de memória contíguos.</span><span class="sxs-lookup"><span data-stu-id="81806-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="81806-179"><xref:System.Span%601> também oferece um melhor desempenho que <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="81806-180">Por fim, é possível usar a propriedade <xref:System.Memory%601.Span?displayProperty=nameWithType> para converter uma instância de <xref:System.Memory%601> em <xref:System.Span%601>, embora a conversão de Span\<T> em Memory\<T> seja inviável.</span><span class="sxs-lookup"><span data-stu-id="81806-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="81806-181">Portanto, se os chamadores tiverem uma instância de <xref:System.Memory%601>, eles poderão chamar seus métodos com os parâmetros <xref:System.Span%601> de qualquer maneira.</span><span class="sxs-lookup"><span data-stu-id="81806-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="81806-182">Usando um parâmetro de tipo <xref:System.Span%601> em vez de o tipo <xref:System.Memory%601>, você pode também escrever uma implementação correta do método de consumo.</span><span class="sxs-lookup"><span data-stu-id="81806-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="81806-183">Você receberá automaticamente verificações de tempo de compilação para garantir que não esteja tentando acessar o buffer, além da concessão do método (saiba mais sobre isso a seguir).</span><span class="sxs-lookup"><span data-stu-id="81806-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="81806-184">Às vezes, você terá que usar um parâmetro <xref:System.Memory%601> em vez de um parâmetro <xref:System.Span%601>, mesmo que esteja totalmente síncrono.</span><span class="sxs-lookup"><span data-stu-id="81806-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="81806-185">Talvez uma API da qual você dependa aceite apenas argumentos <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="81806-186">Isso é possível, mas conheça as vantagens e desvantagens envolvidas com o uso de <xref:System.Memory%601> de maneira síncrona.</span><span class="sxs-lookup"><span data-stu-id="81806-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="81806-187">**Regra 2: usar ReadOnlySpan\<T> ou ReadOnlyMemory\<T>, se o buffer for somente leitura.**</span><span class="sxs-lookup"><span data-stu-id="81806-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="81806-188">Nos exemplos anteriores, o método `DisplayBufferToConsole` apenas lê no buffer, sem modificar o respectivo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="81806-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="81806-189">A assinatura do método deve ser alterada para a seguinte.</span><span class="sxs-lookup"><span data-stu-id="81806-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="81806-190">Na verdade, se combinarmos esta regra com a Regra 1, poderemos fazer ainda melhor e reescrever a assinatura do método da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="81806-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="81806-191">O método `DisplayBufferToConsole` agora funciona praticamente com todos os tipos de buffer possíveis: `T[]`, armazenamento alocado com [stackalloc](~/docs/csharp/language-reference/operators/stackalloc.md), e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="81806-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](~/docs/csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="81806-192">Você pode, inclusive, passar um <xref:System.String> diretamente nele!</span><span class="sxs-lookup"><span data-stu-id="81806-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="81806-193">**Regra 3: se o método aceitar o Memory\<T> e retornar `void`, não usar a instância de Memory\<T>, quando o método for retornado.**</span><span class="sxs-lookup"><span data-stu-id="81806-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="81806-194">Isso está relacionado ao conceito de "concessão" mencionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="81806-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="81806-195">A concessão de um retorno de void do método na instância de <xref:System.Memory%601> começa quando o método é inserido e termina quando o método é encerrado.</span><span class="sxs-lookup"><span data-stu-id="81806-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="81806-196">Considere o exemplo a seguir, que chama `Log` em um loop com base na entrada do console.</span><span class="sxs-lookup"><span data-stu-id="81806-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="81806-197">Se `Log` for um método totalmente síncrono, esse código se comportará como esperado porque há apenas um consumidor ativo da instância de memória a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="81806-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="81806-198">Mas imagine que `Log` tenha essa implementação.</span><span class="sxs-lookup"><span data-stu-id="81806-198">But imagine instead that `Log` has this implementation.</span></span>

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

<span data-ttu-id="81806-199">Nesta implementação, `Log` viola a respectiva concessão porque ela ainda tenta usar a instância de <xref:System.Memory%601> em segundo plano, após o método original ter retornado.</span><span class="sxs-lookup"><span data-stu-id="81806-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="81806-200">O método `Main` pode alterar o buffer enquanto `Log` tenta ler nele, o que pode resultar em dados corrompidos.</span><span class="sxs-lookup"><span data-stu-id="81806-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="81806-201">Há várias maneiras de resolver isso:</span><span class="sxs-lookup"><span data-stu-id="81806-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="81806-202">O método `Log` pode retornar uma classe <xref:System.Threading.Tasks.Task> em vez de `void`, assim como faz a seguinte implementação do método `Log`.</span><span class="sxs-lookup"><span data-stu-id="81806-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="81806-203">É possível implementar `Log` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="81806-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="81806-204">**Regra 4: se o método aceitar o Memory\<T> e retornar uma classe Task, não usar a instância de Memory\<T> quando a classe Task passar para um estado terminal.**</span><span class="sxs-lookup"><span data-stu-id="81806-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="81806-205">Esta é apenas a variante assíncrona da Regra 3.</span><span class="sxs-lookup"><span data-stu-id="81806-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="81806-206">O método `Log` do exemplo anterior pode ser escrito da seguinte forma para cumprir esta regra:</span><span class="sxs-lookup"><span data-stu-id="81806-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="81806-207">Nesse caso, "estado terminal" significa que a tarefa passa para um estado concluído, com falha ou cancelado.</span><span class="sxs-lookup"><span data-stu-id="81806-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="81806-208">Em outras palavras, "estado terminal" significa "qualquer coisa que cause atraso de lançamento ou continuação de execução".</span><span class="sxs-lookup"><span data-stu-id="81806-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="81806-209">Essa orientação se aplica a métodos que retornam <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601> ou outros tipos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="81806-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="81806-210">**Regra 5: se o construtor aceitar o Memory\<T> como parâmetro, os métodos da instância no objeto construído serão considerados consumidores da instância de Memory\<T>.**</span><span class="sxs-lookup"><span data-stu-id="81806-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="81806-211">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="81806-211">Consider the following example:</span></span>

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

<span data-ttu-id="81806-212">Nesse caso, o construtor `OddValueExtractor` aceita um `ReadOnlyMemory<int>` como parâmetro, para que o próprio construtor seja um consumidor da instância de `ReadOnlyMemory<int>`, e todos os métodos da instância no valor retornado também sejam consumidores da instância original de `ReadOnlyMemory<int>`.</span><span class="sxs-lookup"><span data-stu-id="81806-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="81806-213">Isso significa que `TryReadNextOddValue` consome a instância de `ReadOnlyMemory<int>`, mesmo que a instância não seja passada diretamente para o método `TryReadNextOddValue`.</span><span class="sxs-lookup"><span data-stu-id="81806-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="81806-214">**Regra 6: quando há uma propriedade tipada configurável de Memory\<T> (ou um método de instância equivalente) no tipo, presume-se que os métodos da instância nesse objeto sejam consumidores da instância de Memory\<T>.**</span><span class="sxs-lookup"><span data-stu-id="81806-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="81806-215">Na verdade, esta é apenas uma variante da Regra 5.</span><span class="sxs-lookup"><span data-stu-id="81806-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="81806-216">Esta regra existe porque presume-se que os setters de propriedade ou métodos equivalentes devam capturar e persistir as respectivas entradas, de modo que os métodos da instância no mesmo objeto possam usar o estado capturado.</span><span class="sxs-lookup"><span data-stu-id="81806-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="81806-217">O exemplo a seguir aciona esta regra:</span><span class="sxs-lookup"><span data-stu-id="81806-217">The following example triggers this rule:</span></span>

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

<span data-ttu-id="81806-218">**Regra 7: quando há uma referência de IMemoryOwner\<T>, é necessário descartá-la ou transferir a propriedade (mas não ambos), em algum momento.**</span><span class="sxs-lookup"><span data-stu-id="81806-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="81806-219">Como uma instância de <xref:System.Memory%601> pode ter suporte de memória gerenciada e não gerenciada, o proprietário deve chamar <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> quando concluir o trabalho realizado na instância de <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="81806-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="81806-220">Como alternativa, o proprietário pode transferir a propriedade da instância de <xref:System.Buffers.IMemoryOwner%601> para um componente diferente, até que o componente receptor se torne responsável por chamar <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> no tempo adequado (saiba mais sobre isso a seguir).</span><span class="sxs-lookup"><span data-stu-id="81806-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="81806-221">Uma falha ao chamar o método <xref:System.Buffers.MemoryPool%601.Dispose%2A> pode causar perdas de memória não gerenciada ou outra degradação do desempenho.</span><span class="sxs-lookup"><span data-stu-id="81806-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="81806-222">Esta regra também se aplica ao código que chama métodos de fábrica, como <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81806-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81806-223">O chamador se torna proprietário do <xref:System.Buffers.IMemoryOwner%601> retornado e fica responsável pelo descarte da instância após concluída.</span><span class="sxs-lookup"><span data-stu-id="81806-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="81806-224">**Regra 8: se tiver um parâmetro IMemoryOwner\<T> na superfície da API, então você estará aceitando a propriedade dessa instância.**</span><span class="sxs-lookup"><span data-stu-id="81806-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="81806-225">Aceitar uma instância desse tipo indica que o componente pretende se apropriar dessa instância.</span><span class="sxs-lookup"><span data-stu-id="81806-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="81806-226">O componente se torna responsável pelo descarte adequado de acordo com a Regra 7.</span><span class="sxs-lookup"><span data-stu-id="81806-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="81806-227">Os componentes que transferem a propriedade da instância de <xref:System.Buffers.IMemoryOwner%601> para um componente diferente não devem mais usar essa instância após a conclusão da chamada do método.</span><span class="sxs-lookup"><span data-stu-id="81806-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81806-228">Se o construtor aceitar <xref:System.Buffers.IMemoryOwner%601> como parâmetro, o respectivo tipo deverá implementar <xref:System.IDisposable>, e o método <xref:System.IDisposable.Dispose%2A> deverá chamar <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81806-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="81806-229">**Regra 9: se estiver encapsulando um método de P/Invoke síncrono, a API deverá aceitar Span\<T> como parâmetro.**</span><span class="sxs-lookup"><span data-stu-id="81806-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="81806-230">De acordo com a Regra 1, <xref:System.Span%601> geralmente é o tipo correto a ser usado para APIs síncronas.</span><span class="sxs-lookup"><span data-stu-id="81806-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="81806-231">Você pode fixar instâncias do <xref:System.Span%601> por meio da palavra-chave [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md), como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="81806-231">You can pin <xref:System.Span%601> instances via the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="81806-232">No exemplo anterior, `pbData` poderá ser nulo, se o alcance da entrada estiver vazio.</span><span class="sxs-lookup"><span data-stu-id="81806-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="81806-233">Se o método exportado exigir que `pbData` seja não nulo, mesmo que `cbData` seja 0, o método poderá ser implementado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="81806-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="81806-234">**Regra 10: se estiver encapsulando um método de P/Invoke assíncrono, a API deverá aceitar Memory\<T> como parâmetro.**</span><span class="sxs-lookup"><span data-stu-id="81806-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="81806-235">Como não é possível usar a palavra-chave [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) em operações assíncronas, use o método <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> para fixar instâncias de <xref:System.Memory%601>, independentemente do tipo de memória contígua que a instância representar.</span><span class="sxs-lookup"><span data-stu-id="81806-235">Since you cannot use the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="81806-236">O exemplo a seguir mostra como usar esta API para executar uma chamada de P/Invoke assíncrona.</span><span class="sxs-lookup"><span data-stu-id="81806-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)state;
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a><span data-ttu-id="81806-237">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81806-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
