---
title: Interface IHostAssemblyStore
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3714f31d0ab58584a8671055cf4c607f04a832c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611053"
---
# <a name="ihostassemblystore-interface"></a>Interface IHostAssemblyStore
Fornece métodos que permitem que um host carregar assemblies e módulos independentemente do common language runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Obtém uma referência a um assembly que não é referenciado pela [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retornado de uma chamada para [ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[Método ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Resolve um módulo dentro de um assembly ou um arquivo de recurso (não inserido) vinculado.|  
  
## <a name="remarks"></a>Comentários  
 `IHostAssemblyStore` Fornece uma maneira para um host carregar assemblies com eficiência com base na identidade do assembly. O host carrega assemblies, retornando `IStream` instâncias que apontam diretamente para os bytes.  
  
 O CLR determina se um host tiver implementado `IHostAssemblyStore` chamando `IHostAssemblyManager::GetNonHostAssemblyStores` na inicialização. Isso permite que o host, por exemplo, para controlar a associação para assemblies de usuário, mas contar com o tempo de execução para associar aos assemblies do .NET Framework.  
  
> [!NOTE]
>  No fornecimento de uma implementação de `IHostAssemblyStore`, o host especifica sua intenção de resolver todos os assemblies que não são referenciados pela `ICLRAssemblyReferenceList` retornados de `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  O .NET Framework versão 2.0 não fornece uma maneira para o host carregar a imagem nativa de um assembly, conforme fornecido pelo [gerador de imagem nativa (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utilitário.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
