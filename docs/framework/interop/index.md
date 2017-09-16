---
title: "Interoperação com código não gerenciado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ff86b062efddde6f97555efb97247f60a6e1db98
ms.contentlocale: pt-br
ms.lasthandoff: 09/08/2017

---
# <a name="interoperating-with-unmanaged-code"></a>Interoperação com código não gerenciado
O .NET Framework promove a interação com componentes COM, serviços COM+, bibliotecas de tipos externas e muitos serviços do sistema operacional. Tipos de dados, assinaturas de método e mecanismos de tratamento de erros variam entre modelos de objetos gerenciados e não gerenciados. Para simplificar a interoperação entre componentes do .NET Framework e o código não gerenciado e para facilitar o caminho de migração, o Common Language Runtime oculta de clientes e servidores as diferenças entre esses modelos de objeto.  
  
 O código que é executado sob o controle de tempo de execução é chamado de código gerenciado. Em contraste, o código executado fora do tempo de execução é chamado de código não gerenciado. Componentes COM, interfaces ActiveX e funções da API do Win32 são exemplos de código não gerenciado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Tópicos explicativos sobre interoperação com código não gerenciado](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 Fornece links a todos os Tópicos explicativos encontrados na documentação conceitual para interoperação com código não gerenciado.  
  
 [Expondo componentes do COM ao .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 Descreve como usar componentes COM de aplicativos do .NET Framework.  
  
 [Expondo componentes do .NET Framework ao COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Descreve como usar componentes do .NET Framework de aplicativos COM.  
  
 [Consumindo funções de DLL não gerenciadas](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.  
  
 [Considerações sobre design para interoperação](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 Fornece dicas para escrever componentes COM integrados.  
  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)  
 Descreve o marshaling para invocação de plataforma e interoperabilidade COM.  
  
 [Como mapear HRESULTs e exceções](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 Descreve o mapeamento entre exceções e HRESULTs.  
  
 [Interoperação usando tipos genéricos](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 Descreve o comportamento de tipos genéricos quando usados em interoperabilidade COM.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interoperabilidade COM avançada](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.

