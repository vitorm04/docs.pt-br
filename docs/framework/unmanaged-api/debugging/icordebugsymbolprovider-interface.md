---
title: Interface ICorDebugSymbolProvider
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e9f475ee3c46b8abb94ce7f804cc8b4a8054ec2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423202"
---
# <a name="icordebugsymbolprovider-interface"></a>Interface ICorDebugSymbolProvider
Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetAssemblyImageBytes](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|Lê dados de um assembly mesclado fornecido um endereço virtual relativo (RVA) no assembly mesclado.|  
|[Método GetAssemblyImageMetadata](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Retorna os metadados de um assembly mesclado.|  
|[Método GetCodeRange](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|Obtém o endereço de início do método e o tamanho fornecido um endereço virtual relativo (RVA) em um método.|  
|[Método GetInstanceFieldSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Obtém a instância de símbolos de campo que correspondem a uma assinatura typespec.|  
|[Método GetMergedAssemblyRecords](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Obtém os registros de símbolo para todos os assemblies mesclados.|  
|[Método GetMethodLocalSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Obtém os símbolos do local do método recebe o endereço virtual relativo (RVA) do método.|  
|[Método GetMethodParameterSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|Obtém os símbolos de parâmetro do método recebe o endereço virtual relativo (RVA) do método.|  
|[Método GetMethodProps](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|Retorna informações sobre propriedades de método, como o método token de metadados e informações sobre seus parâmetros genéricos, dado um endereço virtual relativo (RVA) nesse método.|  
|[Método GetObjectSize](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|Retorna o tamanho do objeto para um objeto com base em sua assinatura typespec.|  
|[Método GetStaticFieldSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Obtém os símbolos de campo estático que correspondem a uma assinatura typespec.|  
|[Método GetTypeProps](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Retorna informações sobre propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, dado um endereço virtual relativo (RVA) em uma vtable.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface só está disponível com o .NET Native. Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
