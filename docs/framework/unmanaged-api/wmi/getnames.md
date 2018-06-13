---
title: Função GetNames (referência de API não gerenciada)
description: A função GetNames recupera os nomes das propriedades de um objeto.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 108946428cdfadcfb9c653b7e444bf278dfa2782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461975"
---
# <a name="getnames-function"></a>Função GetNames
Recupera um subconjunto ou todos os nomes das propriedades de um objeto. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`wszQualifierName`  
[in] Um ponteiro para um válida `LPCWSTR` que especifica um nome de qualificador que funciona como parte de um filtro. Para obter mais informações, consulte o [comentários](#remarks) seção. Esse parâmetro pode ser `null`. 

`lFlags`  
[in] Uma combinação de campos de bits. Para obter mais informações, consulte o [comentários](#remarks) seção.

`pQualifierValue`   
[in] Um ponteiro para um válida `VARIANT` estrutura inicializada com um valor de filtro. Esse parâmetro pode ser `null`. 

`pstrNames`  
[out] Um `SAFEARRAY` estrutura que contém os nomes de propriedade. Na entrada, esse parâmetro sempre deve ser um ponteiro para `null`. Consulte o [comentários](#remarks) para obter mais informações. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos ou foi especificada uma combinação incorreta de sinalizadores e parâmetros. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) método.

Nomeado retornados é controlado por uma combinação de sinalizadores e parâmetros. Por exemplo, a função pode retornar os nomes de todas as propriedades ou apenas os nomes das propriedades de chave.  O filtro primário for especificado no `lFlags` parâmetro e os outros parâmetros variam dependendo-lo.

O sinalizador de valores em `lFlags` são campos de bits


Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são campos de bits são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.  Você pode combinar um sinalizador de cada grupo com qualquer sinalizador de nenhum outro grupo. No entanto, os sinalizadores do mesmo grupo são mutuamente exclusivos. 

| Sinalizadores de grupo 1 |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Retorne todos os nomes de propriedade. `strQualifierName` e `pQualifierVal` são utilizadas. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Retornar somente as propriedades que têm um qualificador do nome especificado pelo `strQualifierName` parâmetro. Se este sinalizador é usado, você deve especificar `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Retornar somente as propriedades que não têm um qualificador do nome especificado pelo `strQualifierName` parâmetro. Se este sinalizador é usado, você deve especificar `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Retornar apenas as propriedades que têm um qualificador do nome especificado pelo `wszQualifierName` parâmetro e também ter um valor idêntico ao especificado pelo `pQualifierVal` estrutura. Se esse sinalizador for usado, você deve especificar ambos um `wszQualifierName` e um `pQualifierValue`. |

| Sinalizadores de grupo 2 |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Retorne apenas os nomes de propriedades que definem as chaves. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Retorno apenas nomes de propriedades que são referências de objeto. |

| Grupo 3 sinalizadores |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retorne apenas os nomes de propriedade que pertencem à classe mais derivada. Exclua propriedades das classes pai. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Retorne apenas os nomes de propriedade que pertencem às classes pai. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Retorne apenas os nomes das propriedades do sistema. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Retorne apenas os nomes das propriedades não são do sistema. |

A função sempre aloca um novo `SAFEARRAY` se ele retorna `WBEM_S_NO_ERROR`, e `pstrNames` é sempre definido para apontar para ele. A matriz retornada pode ter elementos 0 se não há propriedades correspondem aos filtros especificados. Se a função retorna um valor diferente de `WBM_S_NO_ERROR`, um novo `SAFEARRAY` estrutura não é retornada.
 
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
