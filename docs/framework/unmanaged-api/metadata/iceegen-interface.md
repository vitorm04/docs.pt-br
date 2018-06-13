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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e3e70749a768377ea470bc44a66b9fdabbb1f93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448850"
---
# <a name="iceegen-interface"></a>Interface ICeeGen
Fornece métodos para compilação de código dinâmico.  
  
 Esta interface está obsoleta e não deve ser usado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Obsoleto. Adiciona uma instrução de .reloc para a base de código.|  
|[Método AllocateMethodBuffer](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Obsoleto. Cria um buffer do tamanho especificado para um método e obtém o endereço virtual relativo do método.|  
|[Método ComputePointer](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Obsoleto. Determina o buffer para a seção de código especificada.|  
|[Método EmitString](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Obsoleto. Emite a cadeia de caracteres especificada para a base de código.|  
|[Método GenerateCeeFile](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Obsoleto. Gera um arquivo de base de código que contém o código base atualmente carregado nisso `ICeeGen`.|  
|[Método GenerateCeeMemoryImage](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Obsoleto. Gera uma imagem na memória para a base de código.|  
|[Método GetIlSection](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Obsoleto. Obtém a seção do código de idioma intermediário base referenciada pelo identificador especificado.|  
|[Método GetIMapTokenIface](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Obsoleto. Obtém a interface referenciada pelo token especificado.|  
|[Método GetMethodBuffer](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Obsoleto. Obtém um buffer de tamanho apropriado para o método no endereço virtual relativo especificado.|  
|[Método GetSectionBlock](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Obsoleto. Obtém um bloco de seção da base de código.|  
|[Método GetSectionCreate](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Obsoleto. Gera e obtém uma seção de código usando o nome especificado e os valores de sinalizador.|  
|[Método GetSectionDataLen](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Obsoleto. Obtém o comprimento da seção especificada.|  
|[Método GetString](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Obsoleto. Obtém a cadeia de caracteres armazenada no endereço virtual relativo especificado.|  
|[Método GetStringSection](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Obsoleto. Obtém uma representação de cadeia de caracteres da seção de código referenciada pelo identificador especificado.|  
|[Método TruncateSection](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Obsoleto. Trunca a seção de código especificado pelo comprimento especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
