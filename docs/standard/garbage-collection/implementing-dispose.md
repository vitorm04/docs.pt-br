---
title: Como implementar um método Dispose
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acc661e8110892dc7daa603ef82b4bc5f167a970
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579438"
---
# <a name="implementing-a-dispose-method"></a>Como implementar um método Dispose

Você implementa um método <xref:System.IDisposable.Dispose%2A> para liberar recursos não gerenciados usados pelo seu aplicativo. O coletor de lixo .NET não alocar nem libera memória não gerenciada.  
  
O padrão para o descarte um objeto, conhecido como [padrão Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md), impõe ordem no tempo de vida de um objeto. O padrão de descarte é usado somente para os objetos que acessam recursos não gerenciados, como identificadores de arquivo e pipe, identificadores de Registro, identificadores de espera ou ponteiros para blocos de memória não gerenciada. Isso ocorre porque o coletor de lixo é muito eficiente para recuperar objetos gerenciados não usados, mas não é capaz de recuperar objetos não gerenciados.  
  
O padrão de descarte tem duas variações:  
  
* Você envolve cada recurso não gerenciado usado por um tipo em um identificador seguro (ou seja, em uma classe derivada de <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). Nesse caso, você implementa a interface <xref:System.IDisposable> e um método `Dispose(Boolean)` adicional. Essa é a variação recomendada e não requer a substituição do método <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
  > [!NOTE]
  > O namespace <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> fornece um conjunto de classes derivadas de <xref:System.Runtime.InteropServices.SafeHandle>, que são listadas na seção [Usando identificadores seguros](#SafeHandles). Se não conseguir encontrar uma classe adequada para liberar seu recurso não gerenciado, você poderá implementar sua própria subclasse de <xref:System.Runtime.InteropServices.SafeHandle>.  
  
* Você implementa a interface <xref:System.IDisposable> e um método `Dispose(Boolean)` adicional, além de substituir o método <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Você deve substituir <xref:System.Object.Finalize%2A> para garantir que os recursos não gerenciados sejam descartados se sua implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> não for chamada por um consumidor do seu tipo. Se você usar a técnica recomendada discutida no item anterior, a classe <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> fará isso em seu nome.  
  
Para ajudar a garantir que os recursos sejam sempre limpos corretamente, um método <xref:System.IDisposable.Dispose%2A> deve poder ser chamado várias vezes sem gerar uma exceção.  
  
O exemplo de código fornecido para o método <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> mostra a agressividade com a qual uma coleta de lixo pode fazer com que um finalizador seja executado enquanto um membro do objeto recuperado ainda está em execução. É uma boa ideia chamar o método <xref:System.GC.KeepAlive%2A> no final de um método <xref:System.IDisposable.Dispose%2A> longo.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() e Dispose(Booliano)  

A interface <xref:System.IDisposable> requer a implementação de um único método sem parâmetros, <xref:System.IDisposable.Dispose%2A>. No entanto, o padrão de descarte requer que dois métodos `Dispose` sejam implementados:  
  
* Uma implementação pública não virtual (`NonInheritable` no Visual Basic) de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> que não possua parâmetros.  
  
* Um método `Overridable` virtual protegido (`Dispose` no Visual Basic) cuja assinatura é:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>A sobrecarga Dispose()

Como o método público, não virtual (`NonInheritable` no Visual Basic) e sem parâmetro `Dispose` é chamado por um consumidor do tipo, sua finalidade é liberar recursos não gerenciados e indicar que o finalizador, se houver um, não precisa ser executado. Por isso, ele tem uma implementação padrão:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
O método `Dispose` executa toda a limpeza do objeto, de modo que o coletor de lixo não precisa mais chamar a substituição dos objetos <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Assim, a chamada para o método <xref:System.GC.SuppressFinalize%2A> impede que o coletor de lixo execute o finalizador. Se o tipo não possuir um finalizador, a chamada para <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> não terá efeito. Observe que o trabalho real de liberar recursos não gerenciado é executado pela segunda sobrecarga do método `Dispose`.  
  
### <a name="the-disposeboolean-overload"></a>A sobrecarga Dispose(Boolean)

Na segunda sobrecarga, o parâmetro *disposing* é um <xref:System.Boolean> que indica se a chamada do método é proveniente de um método <xref:System.IDisposable.Dispose%2A> (seu valor é `true`) ou de um finalizador (seu valor é `false`).  
  
O corpo do método consiste em dois blocos de código:  
  
* Um bloco que libera recursos não gerenciados. Este bloco é executado independentemente do valor do parâmetro `disposing`.  
  
* Um bloco condicional que libera recursos gerenciados. Este bloco será executado se o valor de `disposing` for `true`. Os recursos gerenciados que ele libera podem incluir:  
  
  **Objetos gerenciados que implementam <xref:System.IDisposable>.** O bloco condicional pode ser usado para chamar sua implementação de <xref:System.IDisposable.Dispose%2A>. Se você usou um indicador seguro para encapsular o recurso não gerenciado, é necessário chamar a implementação de <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> aqui.  
  
  **Objetos gerenciados que consomem muita memória ou consomem recursos escassos.** Liberar esses objetos explicitamente no método `Dispose` libera-os mais rápido do que se eles fossem recuperados de forma não determinística pelo coletor de lixo.  
  
Se a chamada do método vier de um finalizador (isto é, se *disposing* for `false`), somente o código que libera os recursos não gerenciados é executado. Como a ordem em que o coletor de lixo destrói objetos gerenciados durante a finalização não é definida, chamar essa sobrecarga `Dispose` com um valor de `false` impede que o finalizador tente liberar os recursos gerenciados que já podem ter sido recuperados.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementando o padrão de descarte para uma classe base

Se você implementar o padrão de descarte para uma classe base, deverá fornecer o seguinte:  
  
> [!IMPORTANT]
> É preciso implementar esse padrão para todas as classes de base que implementam <xref:System.IDisposable.Dispose> e não são `sealed` (`NotInheritable` no Visual Basic).  
  
* Uma implementação de <xref:System.IDisposable.Dispose%2A> que chame o método `Dispose(Boolean)`.  
  
* Um método `Dispose(Boolean)` que execute o trabalho real de liberar recursos.  
  
* Uma classe derivada de <xref:System.Runtime.InteropServices.SafeHandle> que envolva o recurso não gerenciado (recomendado) ou uma substituição para o método <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. A classe <xref:System.Runtime.InteropServices.SafeHandle> fornece um finalizador que o libera de ter que codificar um.  
  
Aqui está o padrão geral para implementar o padrão de descarte para uma classe base que usa um identificador seguro.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> O exemplo anterior usa um objeto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> para ilustrar o padrão; qualquer objeto derivado de <xref:System.Runtime.InteropServices.SafeHandle> poderia ser usado em vez disso. Observe que o exemplo não cria corretamente uma instância de seu objeto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
Aqui está o padrão geral para implementar o padrão de descarte para uma classe base que substitui <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> No C#, você deve substituir <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definindo um [destruidor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementando o padrão de descarte para uma classe derivada

Uma classe derivada de uma classe que implementa a interface <xref:System.IDisposable> não deve implementar <xref:System.IDisposable> porque a implementação da classe base <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> é herdada pelas classes derivadas. Em vez disso, para implementar o padrão de descarte para uma classe derivada, você deverá fornecer o seguinte:  
  
* Um método `protected Dispose(Boolean)` que substitua o método da classe base e execute o trabalho real de liberar os recursos da classe derivada. Esse método também deve chamar o método `Dispose(Boolean)` da classe base e passar para ele um valor de `true` para o argumento *disposing*.  
  
* Uma classe derivada de <xref:System.Runtime.InteropServices.SafeHandle> que envolva o recurso não gerenciado (recomendado) ou uma substituição para o método <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. A classe <xref:System.Runtime.InteropServices.SafeHandle> fornece um finalizador que o libera de ter que codificar um. Se você fornecer um finalizador, ele deverá chamar a sobrecarga de `Dispose(Boolean)` com um argumento *disposing* de `false`.  
  
Aqui está o padrão geral para implementar o padrão de descarte para uma classe derivada que usa um identificador seguro:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> O exemplo anterior usa um objeto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> para ilustrar o padrão; qualquer objeto derivado de <xref:System.Runtime.InteropServices.SafeHandle> poderia ser usado em vez disso. Observe que o exemplo não cria corretamente uma instância de seu objeto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
Aqui está o padrão geral para implementar o padrão de descarte para uma classe derivada que substitui <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> No C#, você deve substituir <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definindo um [destruidor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Usando identificadores seguros

Escrever código para o finalizador de um objeto é uma tarefa complexa que poderá causar problemas se não for feito corretamente. Assim, recomendamos que você construa objetos <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>, em vez de implementar um finalizador.  
  
As classes derivadas da classe <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> simplificam problemas de vida útil de objetos ao atribuir e liberar identificadores sem interrupção. Elas contêm um finalizador crítico que certamente será executado enquanto um domínio de aplicativo estiver descarregando. Para obter mais informações sobre as vantagens de usar um identificador seguro, consulte <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. As seguintes classes derivadas no namespace <xref:Microsoft.Win32.SafeHandles> fornecem os identificadores seguros:  
  
* As classes <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> e <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> para arquivos, arquivos mapeados na memória e pipes.  
  
* A classe <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> para exibições de memória.  
  
* As classes <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> e <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> para construtores de criptografia.  
  
* A classe <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> para chaves do registro.  
  
* A classe <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> para identificadores de espera.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Usando um identificador seguro para implementar o padrão de descarte para uma classe base

O exemplo a seguir ilustra o padrão de descarte para uma classe base, `DisposableStreamResource`, a qual usa um identificador seguro para encapsular recursos não gerenciados. Define uma classe `DisposableResource` que usa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> para encapsular um objeto <xref:System.IO.Stream> que representa um arquivo aberto. O método `DisposableResource` também inclui uma única propriedade, `Size`, a qual retorna o número total de bytes no fluxo de arquivos.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Usando um identificador seguro para implementar o padrão de descarte para uma classe derivada

O exemplo a seguir ilustra o padrão de descarte para uma classe derivada, `DisposableStreamResource2`, que herda da classe `DisposableStreamResource` apresentada no exemplo anterior. A classe acrescenta um método adicional, `WriteFileInfo`, e usa um objeto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> para encapsular o identificador do arquivo gravável.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Consulte também

<xref:System.GC.SuppressFinalize%2A>   
<xref:System.IDisposable>   
<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>   
<xref:Microsoft.Win32.SafeHandles>   
<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>   
<xref:System.Object.Finalize%2A?displayProperty=nameWithType>   
[Como definir e consumir classes e structs (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)   
[Padrão de descarte](../../../docs/standard/design-guidelines/dispose-pattern.md)
