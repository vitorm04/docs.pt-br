---
title: Interface ICeeGen
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426156"
---
# <a name="iceegen-interface"></a>Interface ICeeGen
Fornece métodos para a compilação dinâmica de código.  
  
 Esta interface está obsoleta e não deve ser usada.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Obsoleto. Adiciona uma instrução. realocação à base de código.|  
|[Método AllocateMethodBuffer](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Obsoleto. Cria um buffer do tamanho especificado para um método e Obtém o endereço virtual relativo do método.|  
|[Método ComputePointer](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Obsoleto. Determina o buffer para a seção de código especificada.|  
|[Método EmitString](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Obsoleto. Emite a cadeia de caracteres especificada na base de código.|  
|[Método GenerateCeeFile](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Obsoleto. Gera um arquivo de base de código que contém a base de código atualmente carregada nesse `ICeeGen`.|  
|[Método GenerateCeeMemoryImage](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Obsoleto. Gera uma imagem na memória para a base de código.|  
|[Método GetIlSection](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Obsoleto. Obtém a seção da base de código de linguagem intermediária referenciada pelo identificador especificado.|  
|[Método GetIMapTokenIface](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Obsoleto. Obtém a interface referenciada pelo token especificado.|  
|[Método GetMethodBuffer](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Obsoleto. Obtém um buffer do tamanho apropriado para o método no endereço virtual relativo especificado.|  
|[Método GetSectionBlock](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Obsoleto. Obtém um bloco de seção da base de código.|  
|[Método GetSectionCreate](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Obsoleto. Gera e obtém uma seção de código usando os valores de nome e sinalizador especificados.|  
|[Método GetSectionDataLen](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Obsoleto. Obtém o comprimento da seção especificada.|  
|[Método GetString](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Obsoleto. Obtém a cadeia de caracteres armazenada no endereço virtual relativo especificado.|  
|[Método GetStringSection](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Obsoleto. Obtém uma representação de cadeia de caracteres da seção de código referenciada pelo identificador especificado.|  
|[Método TruncateSection](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Obsoleto. Trunca a seção de código especificada pelo comprimento especificado.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
