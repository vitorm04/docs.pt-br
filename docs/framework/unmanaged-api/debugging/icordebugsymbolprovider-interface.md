---
title: Interface ICorDebugSymbolProvider
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa30391f10a5f9540090e90500c1cb0a9a410b1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955524"
---
# <a name="icordebugsymbolprovider-interface"></a>Interface ICorDebugSymbolProvider
Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetAssemblyImageBytes](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|Lê dados de um assembly mesclado, dado um endereço virtual relativo (RVA) no assembly mesclado.|  
|[Método GetAssemblyImageMetadata](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Retorna os metadados de um assembly mesclado.|  
|[Método GetCodeRange](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|Obtém o endereço inicial e o tamanho do método de acordo com um endereço virtual relativo (RVA) em um método.|  
|[Método GetInstanceFieldSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Obtém os símbolos de campo de instância que correspondem a uma assinatura de TypeSpec.|  
|[Método GetMergedAssemblyRecords](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Obtém os registros de símbolo de todos os assemblies mesclados.|  
|[Método GetMethodLocalSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Obtém os símbolos locais de um método de acordo com o endereço virtual relativo (RVA) desse método.|  
|[Método GetMethodParameterSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|Obtém os símbolos de parâmetro de um método de acordo com o endereço virtual relativo (RVA) desse método.|  
|[Método GetMethodProps](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.|  
|[Método GetObjectSize](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|Retorna o tamanho do objeto de um objeto com base em sua assinatura de TypeSpec.|  
|[Método GetStaticFieldSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Obtém os símbolos de campo estático que correspondem a uma assinatura de TypeSpec.|  
|[Método GetTypeProps](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Retorna informações sobre as propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
