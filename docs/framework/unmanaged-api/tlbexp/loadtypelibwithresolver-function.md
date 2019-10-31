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
ms.openlocfilehash: 82fa0903474ee04b767fd9c68812efe7f0cc4fa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124156"
---
# <a name="loadtypelibwithresolver-function"></a>Função LoadTypeLibWithResolver
Carrega uma biblioteca de tipos e usa a [interface ITypeLibResolver](itypelibresolver-interface.md) fornecida para resolver quaisquer bibliotecas de tipos referenciadas internamente.  
  
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
  
- `REGKIND_DEFAULT`: usar o comportamento de registro padrão.  
  
- `REGKIND_REGISTER`: registre essa biblioteca de tipos.  
  
- `REGKIND_NONE`: não Registre esta biblioteca de tipos.  
  
 `pTlbResolver`  
 no Um ponteiro para a implementação da [interface ITypeLibResolver](itypelibresolver-interface.md).  
  
 `pptlib`  
 fora Uma referência à biblioteca de tipos que está sendo carregada.  
  
## <a name="return-value"></a>Valor retornado  
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
 O [Tlbexp. exe (tipo de exportador da biblioteca de tipos)](../../tools/tlbexp-exe-type-library-exporter.md) chama a função `LoadTypeLibWithResolver` durante o processo de conversão assembly-to-Type-Library.  
  
 Essa função carrega a biblioteca de tipos especificada com acesso mínimo ao registro. Em seguida, a função examina a biblioteca de tipos para bibliotecas de tipos referenciadas internamente, cada uma delas deve ser carregada e adicionada à biblioteca de tipos pai.  
  
 Antes que uma biblioteca de tipos referenciada possa ser carregada, seu caminho de arquivo de referência deve ser resolvido para um caminho de arquivo completo. Isso é feito por meio do [Método ResolveTypeLib](resolvetypelib-method.md) que é fornecido pela [interface ITypeLibResolver](itypelibresolver-interface.md), que é passada no parâmetro `pTlbResolver`.  
  
 Quando o caminho completo do arquivo da biblioteca de tipos referenciado é conhecido, a função `LoadTypeLibWithResolver` carrega e adiciona a biblioteca de tipos referenciada à biblioteca de tipos pai, criando uma biblioteca de tipos mestre combinada.  
  
 Depois que a função resolve e carrega todas as bibliotecas de tipos referenciadas internamente, ela retorna uma referência à biblioteca de tipos resolvida Master no parâmetro `pptlib`.  
  
 A função `LoadTypeLibWithResolver` é geralmente chamada pelo [Tlbexp. exe (tipo exportador da biblioteca de tipos)](../../tools/tlbexp-exe-type-library-exporter.md), que fornece sua própria implementação de [interface ITypeLibResolver](itypelibresolver-interface.md) interna no parâmetro `pTlbResolver`.  
  
 Se você chamar `LoadTypeLibWithResolver` diretamente, deverá fornecer sua própria implementação de [interface ITypeLibResolver](itypelibresolver-interface.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef. h  
  
 **Biblioteca:** TlbRef. lib  
  
 **Versão do .NET Framework:** 3,5, 3,0, 2,0  
  
## <a name="see-also"></a>Consulte também

- [Funções auxiliares do Tlbexp](index.md)
- [Função LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
