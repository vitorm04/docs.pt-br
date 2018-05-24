---
title: Chamando uma função de DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="calling-a-dll-function"></a>Chamando uma função de DLL
Embora a chamada a funções de DLL não gerenciadas seja quase idêntica à chamada de outro código gerenciado, há diferenças que podem fazer com que as funções de DLL pareçam confusas a princípio. Esta seção apresenta tópicos que descrevem alguns dos problemas incomuns relacionados a chamadas.  
  
 Estruturas retornadas de chamadas de invocação de plataforma devem ser tipos de dados que têm a mesma representação em um código gerenciado e não gerenciado. Esses tipos são chamados de *tipos blittable* porque não exigem conversão (consulte [Tipos blittable e não blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md)). Para chamar uma função que tem uma estrutura não blittable como seu tipo de retorno, é possível definir um tipo de auxiliar blittable do mesmo tamanho do tipo não blittable e converter os dados depois que a função é retornada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Passando estruturas](../../../docs/framework/interop/passing-structures.md)  
 Identifica os problemas de passar estruturas de dados com um layout predefinido.  
  
 [Funções de retorno de chamada](../../../docs/framework/interop/callback-functions.md)  
 Fornece informações básicas sobre as funções de retorno de chamada.  
  
 [Como implementar funções de retorno de chamada](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Descreve como implementar funções de retorno de chamada em um código gerenciado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Consumindo funções de DLL não gerenciadas](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.  
  
 [Marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 Descreve como declarar parâmetros de método e passar argumentos para funções exportadas por bibliotecas não gerenciadas.
