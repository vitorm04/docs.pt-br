---
title: Função _CorDllMain
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c509f475d5bf0105ece9791ee3e51d21c298a31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666906"
---
# <a name="cordllmain-function"></a>\_Função CorDllMain

Inicializa o common language runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho do CLR do assembly da DLL e inicia a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `hInst`  
 [in] O identificador da instância do módulo carregado.  
  
 `dwReason`  
 [in] Indica por que a função de ponto de entrada DLL está sendo chamada. Esse parâmetro pode ser um dos seguintes valores: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ANEXAR ou DLL\_processo\_DESANEXAR. Para obter descrições desses valores, consulte o `DllMain` documentação no SDK da plataforma.  
  
 `lpReserved`  
 [in] Não utilizado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retornará `true` para o sucesso e `false` se ocorrer um erro.  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada pelo carregador do sistema operacional para os assemblies DLL. Para assemblies executáveis, o carregador de chamadas a [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function em vez disso.  
  
 Carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de DLL.  
  
O `_CorDllMain` função é chamada diretamente pelo carregador do sistema operacional.
  
 Para obter mais informações, consulte a seção comentários a [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tópico.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
