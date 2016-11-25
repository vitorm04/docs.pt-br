---
title: "Referências fracas"
description: "Referências fracas"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/19/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 22319f2f-0008-4ace-815e-545892a0512a
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: a966f430c00f07d48f2210d64f03d6805f4e3097

---

# <a name="weak-references"></a>Referências fracas

O coletor de lixo não pode coletar um objeto em uso por um aplicativo enquanto o código do aplicativo pode acessar esse objeto. O aplicativo tem uma referência forte para o objeto. 

Uma referência fraca permite que o coletor de lixo colete o objeto enquanto ainda permite que o aplicativo o acesse. Uma referência fraca é válida somente durante o período indeterminado até que o objeto seja coletado quando não há nenhuma referência forte. Quando você usa uma referência fraca, o aplicativo ainda pode obter uma referência forte para o objeto, o que impede que ele seja coletado. No entanto, sempre há o risco de o coletor de lixo obter o objeto primeiro antes de uma referência forte ser restabelecida.

As referências fracas são úteis para objetos que usam muita memória, mas podem ser facilmente recriados se forem recuperados pela coleta de lixo. 

Suponha que um modo de exibição de árvore exiba uma escolha hierárquica complexa de opções para o usuário. Se os dados subjacentes forem grandes, manter a árvore na memória é ineficiente quando o usuário está envolvido com outra coisa no aplicativo. 

Quando o usuário alterna para outra parte do aplicativo, você pode usar a classe [WeakReference](xref:System.WeakReference) ou [WeakReference&lt;T&gt;](xref:System.WeakReference%601) para criar uma referência fraca para a árvore e destruir todas as referências fortes. Quando o usuário alterna de volta para a árvore, o aplicativo tenta obter uma referência forte para a árvore e, se tiver êxito, evita a reconstrução da árvore.

Para estabelecer uma referência fraca com um objeto, você cria uma [WeakReference](xref:System.WeakReference) usando a instância do objeto a ser rastreada. Em seguida, você deve define a propriedade [Target](xref:System.WeakReference.Target) para aquele objeto e define a referência original para o objeto como null. 

## <a name="short-and-long-weak-references"></a>Referências fracas curtas e longas

Você pode criar uma referência fraca curta ou uma referência fraca longa: 

* Abreviado

  O destino de uma referência fraca curta se torna `null` quando o objeto é recuperado pela coleta de lixo. A referência fraca é um objeto gerenciado e está sujeita à coleta de lixo assim como qualquer outro objeto gerenciado. Uma referência fraca curta é o construtor padrão para [WeakReference](xref:System.WeakReference). 

* Long

  Uma referência fraca longa é mantida após o método [Finalize](xref:System.Object.Finalize) do objeto ter sido chamado. Isso permite que o objeto seja recriado, mas o estado do objeto permanece imprevisível. Para usar uma referência longa, especifique `true` no construtor [WeakReference](xref:System.WeakReference). 

  Se o tipo de objeto não tiver um método [Finalize](xref:System.Object.Finalize), a funcionalidade de referência fraca curta é aplicada e a referência fraca é válida apenas até o destino ser coletado, o que pode ocorrer a qualquer momento após o finalizador ser executado.

Para estabelecer uma referência forte e usar o objeto novamente, converta a propriedade [Target](xref:System.WeakReference.Target) de um [WeakReference](xref:System.WeakReference) para o tipo do objeto. Se a propriedade [Target](xref:System.WeakReference.Target) retornar `null`, o objeto foi coletado, caso contrário, você pode continuar a usar o objeto, pois o aplicativo recuperou uma referência forte para ele.

## <a name="guidelines-for-using-weak-references"></a>Diretrizes para usar referências fracas

Use referências fracas longas somente quando necessário, uma vez que o estado do objeto é imprevisível após a finalização. 

Evite usar referências fracas para objetos pequenos, pois o ponteiro em si pode ser tão grande quanto ou maior. 

Evite usar referências fracas como uma solução automática para problemas de gerenciamento de memória. Em vez disso, desenvolva uma política de cache efetiva para lidar com os objetos do seu aplicativo. 

## <a name="see-also"></a>Consulte também

[Coleta de lixo no .NET](index.md)



<!--HONumber=Nov16_HO3-->


