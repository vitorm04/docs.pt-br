---
title: "Limpando recursos não gerenciados"
description: "Limpando recursos não gerenciados"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8c97c3e2-8619-47ce-ae29-d6a3140bfa83
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 43ad8829de51775b23d1e00d9b4e2a4f4b240e94
ms.lasthandoff: 03/03/2017

---

# <a name="cleaning-up-unmanaged-resources"></a>Limpando recursos não gerenciados

Para a maioria dos objetos criados pelo aplicativo, você pode contar com o coletor de lixo do .NET Framework para lidar com o gerenciamento de memória. No entanto, ao criar objetos que incluem recursos não gerenciados, você deverá liberar os recursos explicitamente assim que terminar de usá-los no aplicativo. Os tipos mais comuns de recursos não gerenciados são objetos que encapsulam recursos do sistema operacional, como arquivos, janelas, conexões de rede ou conexões de bancos de dados. Embora o coletor de lixo consiga controlar o tempo de vida de um objeto que encapsula um recurso não gerenciado, ele não sabe como liberar e limpar o recurso não gerenciado. 

Se seus tipos usam recursos não gerenciados, você deve fazer o seguinte: 

* Implementar o padrão de descarte. Isso exige que você forneça uma implementação de [IDisposable.Dispose](xref:System.IDisposable.Dispose) para habilitar a liberação determinística dos recursos não gerenciados. Um consumidor do seu tipo chama [Dispose](xref:System.IDisposable.Dispose) quando o objeto (e os recursos que ele usa) não são mais necessários. O método [Dispose](xref:System.IDisposable.Dispose) libera imediatamente os recursos não gerenciados. 

* Fazer com que seus recursos não gerenciados sejam liberados se um consumidor do seu tipo esquecer de chamar [Dispose](xref:System.IDisposable.Dispose). Há duas formas de fazer isso: 

    * Usar um identificador seguro para encapsular o recurso não gerenciado. Esta é a técnica recomendada. Os identificadores seguros são derivados da classe [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) e incluem um método [Finalize](xref:System.Object.Finalize) robusto. Ao usar um identificador seguro, você simplesmente implementa a interface [IDisposable](xref:System.IDisposable) e chama o método [Dispose](xref:System.IDisposable.Dispose) do identificador seguro na implementação de [IDisposable.Dispose](xref:System.IDisposable.Dispose). O finalizador do identificador seguro é chamado automaticamente pelo coletor de lixo quando o método [Dispose](xref:System.IDisposable.Dispose) não é chamado. 

      —ou—

    * Substituir o método [Object.Finalize](xref:System.Object.Finalize). A finalização habilita a liberação não determinística de recursos não gerenciados quando o consumidor de um tipo não chama [IDisposable.Dispose](xref:System.IDisposable.Dispose) para descartá-los forma determinista. No entanto, como a finalização de objetos pode ser uma operação complexa e propensa a erros, recomendamos que você use um identificador seguro em vez de fornecer seu próprio finalizador. 

Os consumidores do seu tipo podem chamar a implementação de [IDisposable](xref:System.IDisposable.Dispose) diretamente para liberar a memória usada pelos recursos não gerenciados. Quando você implementa corretamente um método [Dispose](xref:System.IDisposable.Dispose), o método [Finalize](xref:System.Object.Finalize) do identificador seguro ou a própria substituição do método [Object.Finalize](xref:System.Object.Finalize) torna-se uma proteção para limpar os recursos quando o método [Dispose](xref:System.IDisposable.Dispose) não é chamado. 

## <a name="in-this-section"></a>Nesta seção

[Implementing a dispose method (Implementando um método de descarte)](implementing-dispose.md) – Descreve como implementar o padrão de descarte para liberar recursos não gerenciados.

[Using objects that implement IDisposable (Usando objetos que implementam IDisposable)](using-objects.md) – Descreve como os consumidores de um tipo garantem que sua implementação de Dispose seja chamada. Recomendamos o uso da instrução using do C# ou da instrução Using do Visual Basic para fazer isso.

## <a name="reference"></a>Referência

[System.IDisposable](xref:System.IDisposable) – Define o método `Dispose` para liberar recursos não gerenciados.

[Object.Finalize](xref:System.Object.Finalize) – Fornece a finalização de objetos quando os recursos não gerenciados não são liberados pelo método `Dispose`. 

[GC.SuppressFinalize](xref:System.GC#System_GC_SuppressFinalize_System_Object_) – Suprime a finalização. Este método geralmente é chamado de um método `Dispose` para impedir a execução de um finalizador. 

