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
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136976"
---
# <a name="_cordllmain-function"></a>\_função CorDllMain

Inicializa o Common Language Runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly de DLL e começa a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `hInst`  
 no O identificador de instância do módulo carregado.  
  
 `dwReason`  
 no Indica por que a função de ponto de entrada de DLL está sendo chamada. Esse parâmetro pode ser um dos seguintes valores: DLL\_PROCESS_ATTACH, DLL\_THREAD\_anexar, DLL\_THREAD\_ATTACH ou DLL\_processo\_desanexar. Para obter descrições desses valores, consulte a documentação do `DllMain` no Platform SDK.  
  
 `lpReserved`  
 no Não utilizado.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna `true` para êxito e `false` se ocorrer um erro.  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada pelo carregador do sistema operacional para assemblies DLL. Para assemblies executáveis, o carregador chama a função [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) em vez disso.  
  
 O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo DLL.  
  
A função `_CorDllMain` é chamada diretamente pelo carregador do sistema operacional.
  
 Para obter informações adicionais, consulte a seção comentários no tópico [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
