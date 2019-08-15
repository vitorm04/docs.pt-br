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
ms.openlocfilehash: 6b9bec757071a98e085ccdeee3fc66bfc07f52bc
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040160"
---
# <a name="loadtypelibwithresolver-function"></a>Função LoadTypeLibWithResolver
Carrega uma biblioteca de tipos e usa a [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) fornecida para resolver quaisquer bibliotecas de tipos referenciadas internamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szFile`  
 no O caminho do arquivo da biblioteca de tipos.  
  
 `regkind`  
 no Um sinalizador de [Enumeração regkind](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) que controla como a biblioteca de tipos é registrada. Seus valores possíveis são:  
  
- `REGKIND_DEFAULT`: Use o comportamento de registro padrão.  
  
- `REGKIND_REGISTER`: Registre esta biblioteca de tipos.  
  
- `REGKIND_NONE`: Não registre esta biblioteca de tipos.  
  
 `pTlbResolver`  
 no Um ponteiro para a implementação da [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 fora Uma referência à biblioteca de tipos que está sendo carregada.  
  
## <a name="return-value"></a>Valor de retorno  
 Um dos valores HRESULT listados na tabela a seguir.  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_OUTOFMEMORY`|Sem memória.|  
|`E_POINTER`|Um ou mais ponteiros são inválidos.|  
|`E_INVALIDARG`|Um ou mais argumentos são inválidos.|  
|`TYPE_E_IOERROR`|A função não pôde gravar no arquivo.|  
|`TYPE_E_REGISTRYACCESS`|Não foi possível abrir o banco de dados de registro do sistema.|  
|`TYPE_E_INVALIDSTATE`|Não foi possível abrir a biblioteca de tipos.|  
|`TYPE_E_CANTLOADLIBRARY`|Não foi possível carregar a biblioteca de tipos ou a DLL.|  
  
## <a name="remarks"></a>Comentários  
 O [Tlbexp. exe (tipo](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) de exportador da biblioteca de `LoadTypeLibWithResolver` tipos) chama a função durante o processo de conversão de assembly para tipo de biblioteca.  
  
 Essa função carrega a biblioteca de tipos especificada com acesso mínimo ao registro. Em seguida, a função examina a biblioteca de tipos para bibliotecas de tipos referenciadas internamente, cada uma delas deve ser carregada e adicionada à biblioteca de tipos pai.  
  
 Antes que uma biblioteca de tipos referenciada possa ser carregada, seu caminho de arquivo de referência deve ser resolvido para um caminho de arquivo completo. Isso é feito por meio do [Método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) que é fornecido pela [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), que é `pTlbResolver` passada no parâmetro.  
  
 Quando o caminho completo do arquivo da biblioteca de tipos referenciado é conhecido `LoadTypeLibWithResolver` , a função carrega e adiciona a biblioteca de tipos referenciada à biblioteca de tipos pai, criando uma biblioteca de tipos mestre combinada.  
  
 Depois que a função resolve e carrega todas as bibliotecas de tipos referenciadas internamente, ela retorna uma referência à biblioteca de tipos do mestre `pptlib` resolvido no parâmetro.  
  
 A `LoadTypeLibWithResolver` função é geralmente chamada pelo [Tlbexp. exe (tipo](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)de exportador da biblioteca de tipos), que fornece sua própria implementação de `pTlbResolver` [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) interna no parâmetro.  
  
 Se você chamar `LoadTypeLibWithResolver` diretamente, deverá fornecer sua própria implementação de [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef.h  
  
 **Biblioteca** TlbRef.lib  
  
 **Versão do .NET Framework:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Consulte também

- [Funções auxiliares do Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [Função LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
