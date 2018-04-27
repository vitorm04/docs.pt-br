---
title: Conceitos de serialização
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 038e150e167da62c7e67d59eb1f460237851ed87
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="serialization-concepts"></a>Conceitos de serialização
Por que você deveria usar serialização? As duas razões mais importantes são persistir o estado de um objeto para uma mídia de armazenamento para que uma cópia exata possa ser recriada em uma etapa posterior e enviar o objeto por valor de um domínio de aplicativo para outro. Por exemplo, a serialização é usada para salvar o estado da sessão no ASP.NET e copiar objetos para a área de transferência no Windows Forms. Ela também é usada remotamente para passar objetos por valor de um domínio de aplicativo para outro.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Armazenamento persistente
Geralmente é necessário armazenar o valor dos campos de um objeto em disco e, em seguida, posteriormente recuperar esses dados. Embora isso seja fácil de atingir sem depender de serialização, essa abordagem é geralmente trabalhosa e sujeita a erros, e torna-se progressivamente mais complexa quando você precisa rastrear a hierarquia de objetos. Imagine escrever um grande aplicativo comercial, que contém milhares de objetos, e ter que escrever código para salvar e restaurar os campos e as propriedades para e do disco para cada objeto. A serialização fornece um mecanismo conveniente para atingir esse objetivo.

O Common Language Runtime gerencia como os objetos são armazenados na memória e fornece um mecanismo de serialização automatizada usando a [reflexão](../../../docs/framework/reflection-and-codedom/reflection.md). Quando um objeto é serializado, o nome da classe, o assembly e todos os membros de dados da instância de classe são gravados para armazenamento. Os objetos geralmente armazenam referências a outras instâncias em variáveis de membros. Quando a classe é serializada, o mecanismo de serialização rastreia objetos referenciados, já serializados, para garantir que o mesmo objeto não seja serializado mais de uma vez. A arquitetura de serialização fornecida com o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] administra corretamente grafos de objeto e referências circulares automaticamente. O único requisito colocado em gráficos de objeto é que todos os objetos, referenciados pelo objeto serializado, também devem ser marcados como `Serializable` (para obter mais informações, consulte [Serialização básica](basic-serialization.md)). Se isso não for feito, uma exceção será gerada quando o serializador tentar serializar o objeto não marcado.

Quando a classe serializada for desserializada, a classe será recriada e os valores de todos os membros de dados serão automaticamente restaurados.

## <a name="marshal-by-value"></a>Marshaling por valor
Os objetos são válidos somente no domínio do aplicativo onde eles são criados. Qualquer tentativa de passar o objeto como um parâmetro ou retorná-lo como resultado falhará a menos que o objeto derive de `MarshalByRefObject` ou esteja marcado como `Serializable`. Se o objeto for marcado como `Serializable`, o objeto automaticamente será serializável, transportado de um domínio de aplicativo para o outro e, em seguida, desserializado para produzir uma cópia exata do objeto no segundo domínio de aplicativo. Esse processo é geralmente chamado de marshaling por valor.
 
Quando um objeto deriva de `MarshalByRefObject`, uma referência de objeto é passada de um domínio de aplicativo para outro, em vez de o próprio objeto. Você também pode marcar um objeto que deriva de `MarshalByRefObject` como `Serializable`. Quando esse objeto é usado como remoto, o formatador responsável pela serialização, que foi pré-configurada com um seletor substituto (`SurrogateSelector`), assume o controle do processo de serialização e substitui todos os objetos derivados de `MarshalByRefObject` com um proxy. Sem o `SurrogateSelector` no lugar, a arquitetura de serialização segue as regras de serialização padrão descritas em [Etapas no processo de serialização](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>Seções relacionadas  
 [Serialização binária](../../../docs/standard/serialization/binary-serialization.md)  
 Descreve o mecanismo de serialização binária que está incluído com o Common Language Runtime.  
  
 [Objetos remotos](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
 Descreve os vários métodos de comunicação disponíveis no .NET Framework para comunicações remotas.  
  
 [Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Descreve o mecanismo de serialização de XML e SOAP que está incluído com o Common Language Runtime.
