---
title: Limpando recursos não gerenciados
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e32d2d4424d05b95af1eda400974da3293b8499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cleaning-up-unmanaged-resources"></a>Limpando recursos não gerenciados
Para a maioria dos objetos criados pelo aplicativo, você pode contar com o coletor de lixo do .NET Framework para lidar com o gerenciamento de memória. No entanto, ao criar objetos que incluem recursos não gerenciados, você deverá liberar os recursos explicitamente assim que terminar de usá-los no aplicativo. Os tipos mais comuns de recursos não gerenciados são objetos que encapsulam recursos do sistema operacional, como arquivos, janelas, conexões de rede ou conexões de bancos de dados. Embora o coletor de lixo consiga controlar o tempo de vida de um objeto que encapsula um recurso não gerenciado, ele não sabe como liberar e limpar o recurso não gerenciado.  
  
 Se seus tipos usam recursos não gerenciados, você deve fazer o seguinte:  
  
-   Implementar o [padrão de descarte](../../../docs/standard/design-guidelines/dispose-pattern.md). Isso exige que você forneça uma implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> para habilitar a liberação determinística dos recursos não gerenciados. Um consumidor do seu tipo chama <xref:System.IDisposable.Dispose%2A> quando o objeto (e os recursos que ele usa) não são mais necessários. O método <xref:System.IDisposable.Dispose%2A> libera imediatamente os recursos não gerenciados.  
  
-   Fazer com que seus recursos não gerenciados sejam liberados se um consumidor do seu tipo esquecer chamar <xref:System.IDisposable.Dispose%2A>. Há duas formas de fazer isso:  
  
    -   Usar um identificador seguro para encapsular o recurso não gerenciado. Esta é a técnica recomendada. Os identificadores seguros são derivados da classe <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> e incluem um método <xref:System.Object.Finalize%2A> robusto. Ao usar um identificador seguro, você simplesmente implementa a interface <xref:System.IDisposable> e chama o método <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> do seu identificador seguro em sua implementação do <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>. O finalizador do identificador seguro é chamado automaticamente pelo coletor de lixo quando seu método <xref:System.IDisposable.Dispose%2A> não é chamado.  
  
         —ou—  
  
    -   Substituir o método <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. A finalização habilita a liberação não determinística de recursos não gerenciados quando o consumidor de um tipo não chama <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> para fazer o descarte de forma determinística. No entanto, como a finalização de objetos pode ser uma operação complexa e propensa a erros, recomendamos que você use um identificador seguro em vez de fornecer seu próprio finalizador.  
  
 Os consumidores do seu tipo poderão então chamar sua implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> diretamente para liberar a memória usada pelos recursos não gerenciados. Quando você implementa corretamente um método <xref:System.IDisposable.Dispose%2A>, o método <xref:System.Object.Finalize%2A> do seu identificador seguro ou sua própria substituição do método <xref:System.Object.Finalize%2A?displayProperty=nameWithType> torna-se uma proteção para limpar recursos para o caso do método <xref:System.IDisposable.Dispose%2A> não ser chamado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementando um método dispose](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 Descreve como implementar o [padrão de descarte](../../../docs/standard/design-guidelines/dispose-pattern.md) para liberar recursos não gerenciados.  
  
 [Usando objetos que implementam IDisposable](../../../docs/standard/garbage-collection/using-objects.md)  
 Descreve como os consumidores de um tipo garantem que sua implementação de <xref:System.IDisposable.Dispose%2A> seja chamada. Recomendamos usar a instrução `using` do C# ou a instrução `Using` do Visual Basic para fazer isso.  
  
## <a name="reference"></a>Referência  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 Define o método <xref:System.IDisposable.Dispose%2A> para liberar recursos não gerenciados.  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 Cuida da finalização de objetos quando os recursos não gerenciados não são liberados pelo método <xref:System.IDisposable.Dispose%2A>.  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 Suprime a finalização. Este método geralmente é chamado de um método `Dispose` para impedir a execução de um finalizador.
