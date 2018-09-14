---
title: Função LoadTypeLibWithResolver
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6a217e2212bb900d7ba83ccdd9cb00d30454baf
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560575"
---
# <a name="loadtypelibwithresolver-function"></a>Função LoadTypeLibWithResolver
Carrega uma biblioteca de tipos e usa fornecido [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipos referenciados internamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szFile`  
 [in] O caminho do arquivo da biblioteca de tipos.  
  
 `regkind`  
 [in] Um [enumeração REGKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) sinalizador que controla como a biblioteca de tipos é registrada. Seus valores possíveis são:  
  
-   `REGKIND_DEFAULT`: Use o comportamento de registro padrão.  
  
-   `REGKIND_REGISTER`: Registre esta biblioteca de tipos.  
  
-   `REGKIND_NONE`: Não registre a biblioteca de tipos.  
  
 `pTlbResolver`  
 [in] Um ponteiro para a implementação de [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Uma referência à biblioteca de tipos que está sendo carregada.  
  
## <a name="return-value"></a>Valor de retorno  
 Um dos valores HRESULT listados na tabela a seguir.  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_OUTOFMEMORY`|Sem memória.|  
|`E_POINTER`|Um ou mais dos ponteiros são inválidos.|  
|`E_INVALIDARG`|Um ou mais argumentos são inválidos.|  
|`TYPE_E_IOERROR`|A função não pôde gravar no arquivo.|  
|`TYPE_E_REGISTRYACCESS`|Não foi possível abrir o banco de dados de registro do sistema.|  
|`TYPE_E_INVALIDSTATE`|Não foi possível abrir a biblioteca de tipos.|  
|`TYPE_E_CANTLOADLIBRARY`|Não foi possível carregar a biblioteca de tipos ou DLL.|  
  
## <a name="remarks"></a>Comentários  
 O [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) chamadas a `LoadTypeLibWithResolver` função durante o processo de conversão de assembly para biblioteca de tipos.  
  
 Essa função carrega a biblioteca de tipo especificado com acesso mínimo ao registro. A função, em seguida, examina a biblioteca de tipos para bibliotecas de tipos referenciados internamente, cada um deles deve ser carregada e adicionada à biblioteca de tipo de pai.  
  
 Antes de uma biblioteca de tipos referenciada pode ser carregada, seu caminho de arquivo de referência deve ser resolvido para um caminho de arquivo completo. Isso é feito por meio do [método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) que é fornecido pela [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), que é passado a `pTlbResolver` parâmetro.  
  
 Quando o caminho completo do arquivo da biblioteca de tipos referenciada é conhecido, o `LoadTypeLibWithResolver` função carrega e adiciona a biblioteca de tipos referenciados na biblioteca de tipo pai, criando uma biblioteca de tipos mestre combinado.  
  
 Depois que a função resolve e carrega todas as bibliotecas de tipos referenciados internamente, ele retornará uma referência à biblioteca de tipo resolvidos mestre no `pptlib` parâmetro.  
  
 O `LoadTypeLibWithResolver` função geralmente é chamada pelo [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que fornece seu próprio interno [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação no `pTlbResolver` parâmetro.  
  
 Se você chamar `LoadTypeLibWithResolver` diretamente, você deve fornecer seu próprio [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef.h  
  
 **Biblioteca:** TlbRef.lib  
  
 **Versão do .NET framework:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Consulte também  
 [Funções auxiliares do Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [Função LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
