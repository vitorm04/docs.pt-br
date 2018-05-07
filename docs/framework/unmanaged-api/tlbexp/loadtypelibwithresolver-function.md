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
ms.openlocfilehash: 751794746e26bd8f0ec2cd6db2f62876e78674e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="loadtypelibwithresolver-function"></a>Função LoadTypeLibWithResolver
Carrega uma biblioteca de tipos e usa fornecido [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipo referenciado internamente.  
  
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
 [in] O caminho do arquivo de biblioteca de tipos.  
  
 `regkind`  
 [in] Um [enumeração REGKIND](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) sinalizador que controla como a biblioteca de tipos é registrada. Os valores possíveis são:  
  
-   `REGKIND_DEFAULT`: Use o comportamento de registro padrão.  
  
-   `REGKIND_REGISTER`: Registre a biblioteca de tipos.  
  
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
|`TYPE_E_IOERROR`|A função não pôde gravar o arquivo.|  
|`TYPE_E_REGISTRYACCESS`|Não foi possível abrir o banco de dados de registro do sistema.|  
|`TYPE_E_INVALIDSTATE`|Não foi possível abrir a biblioteca de tipos.|  
|`TYPE_E_CANTLOADLIBRARY`|Não foi possível carregar a biblioteca de tipos ou DLL.|  
  
## <a name="remarks"></a>Comentários  
 O [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) chama o `LoadTypeLibWithResolver` função durante o processo de conversão de assembly a biblioteca de tipos.  
  
 Essa função carrega a biblioteca com acesso mínimo para registro. A função, em seguida, examina a biblioteca de tipos para bibliotecas de tipo referenciado internamente, cada um deles deve ser carregada e adicionada à biblioteca de tipo de pai.  
  
 Antes de uma biblioteca de tipos referenciada pode ser carregada, seu caminho de arquivo de referência deve ser resolvido para um caminho de arquivo completo. Isso é feito por meio de [método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) que é fornecido pelo [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), que é passado no `pTlbResolver` parâmetro.  
  
 Quando o caminho completo do arquivo da biblioteca de tipos referenciada é conhecido, o `LoadTypeLibWithResolver` função carrega e adiciona a biblioteca de tipos referenciada na biblioteca de tipo de pai, criando uma biblioteca de tipos mestre combinados.  
  
 Depois que a função resolve e carrega todas as bibliotecas de tipo referenciado internamente, ele retorna uma referência à biblioteca de tipo resolvidos mestre no `pptlib` parâmetro.  
  
 O `LoadTypeLibWithResolver` função geralmente é chamada pelo [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que fornece seu próprio interno [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação no `pTlbResolver` parâmetro.  
  
 Se você chamar `LoadTypeLibWithResolver` diretamente, você deve fornecer seu próprio [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef.h  
  
 **Biblioteca:** TlbRef.lib  
  
 **Versão do .NET framework:** 2.0, 3.0, 3.5  
  
## <a name="see-also"></a>Consulte também  
 [Funções auxiliares do Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [Função LoadTypeLibEx](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)
