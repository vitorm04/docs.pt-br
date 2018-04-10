---
title: Interoperação com código não gerenciado
ms.date: 01/17/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 38c569633304ed9e6f86e7a04ef7b0dfa79b6704
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="interoperating-with-unmanaged-code"></a>Interoperação com código não gerenciado

O .NET Framework promove a interação com componentes COM, serviços COM+, bibliotecas de tipos externas e muitos serviços do sistema operacional. Tipos de dados, assinaturas de método e mecanismos de tratamento de erros variam entre modelos de objetos gerenciados e não gerenciados. Para simplificar a interoperação entre componentes do .NET Framework e o código não gerenciado e para facilitar o caminho de migração, o Common Language Runtime oculta de clientes e servidores as diferenças entre esses modelos de objeto.

O código que é executado sob o controle de tempo de execução é chamado de código gerenciado. Em contraste, o código executado fora do tempo de execução é chamado de código não gerenciado. Componentes COM, interfaces ActiveX e funções da API do Win32 são exemplos de código não gerenciado.

## <a name="in-this-section"></a>Nesta seção

[Expondo componentes do COM ao .NET Framework](exposing-com-components.md)  
Descreve como usar componentes COM de aplicativos do .NET Framework.

[Expondo componentes do .NET Framework ao COM](exposing-dotnet-components-to-com.md)  
Descreve como usar componentes do .NET Framework de aplicativos COM.

[Consumindo funções de DLL não gerenciadas](consuming-unmanaged-dll-functions.md)  
Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.

[Marshaling de interoperabilidade](interop-marshaling.md)  
Descreve o marshaling para invocação de plataforma e interoperabilidade COM.

[Como mapear HRESULTs e exceções](how-to-map-hresults-and-exceptions.md)  
Descreve o mapeamento entre exceções e HRESULTs.

[Wrappers COM](com-wrappers.md)  
Descreve os wrappers fornecidos pelo interoperabilidade COM.

[Equivalência de tipos e tipos de interoperabilidade inseridos](type-equivalence-and-embedded-interop-types.md)  
Descreve como as informações de tipo para tipos COM são inseridas em assemblies e como o common language runtime determina a equivalência de tipos COM inseridos.

[Como gerar assemblies de interoperabilidade primários usando Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Descreve como gerar assemblies de interoperabilidade primários usando *Tlbimp.exe* (importador da biblioteca).

[Como registrar assemblies de interoperabilidade primários](how-to-register-primary-interop-assemblies.md)  
Descreve como registrar assemblies de interoperabilidade primários antes de referenciá-las em seus projetos.

[Interoperabilidade COM sem registro](registration-free-com-interop.md)  
Descreve como interoperabilidade ativar componentes sem usar o registro do Windows.

[Como configurar componentes do COM baseados no .NET Framework para ativação sem registro](configure-net-framework-based-com-components-for-reg.md)  
Descreve como criar um manifesto de aplicativo e como criar e inserir um manifesto do componente.
