---
title: Interface IHostAssemblyStore
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c795d4baa3030817299f23c3dadf4caf7a5edc5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystore-interface"></a>Interface IHostAssemblyStore
Fornece métodos que permitem que um host ao carregar assemblies e módulos independentemente do common language runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retornado de uma chamada para [Ihostassemblymanager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[Método ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Resolve um módulo dentro de um assembly ou um arquivo de recurso (não inserido) vinculado.|  
  
## <a name="remarks"></a>Comentários  
 `IHostAssemblyStore`Fornece uma maneira para um host carregar assemblies com eficiência com base na identidade do assembly. O host carrega assemblies retornando `IStream` instâncias que aponte diretamente para os bytes.  
  
 O CLR determina se um host tiver implementado `IHostAssemblyStore` chamando `IHostAssemblyManager::GetNonHostAssemblyStores` na inicialização. Isso permite que o host, por exemplo, para controlar a associação para assemblies de usuário, mas a contar com o tempo de execução para associar a assemblies do .NET Framework.  
  
> [!NOTE]
>  Fornecer uma implementação de `IHostAssemblyStore`, o host especifica sua intenção de resolver todos os assemblies que não são referenciados pelo `ICLRAssemblyReferenceList` retornado de `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  O .NET Framework versão 2.0 não oferece uma maneira para o host carregar a imagem nativa de um assembly, conforme fornecido pelo [gerador de imagem nativa (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utilitário.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
