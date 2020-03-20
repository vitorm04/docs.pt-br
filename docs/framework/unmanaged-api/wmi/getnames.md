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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174947"
---
# <a name="getnames-function"></a>Função GetNames
Recupera um subconjunto ou todos os nomes das propriedades de um objeto.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszQualifierName`  
[em] Um ponteiro para `LPCWSTR` um válido que especifica um nome qualificador que funciona como parte de um filtro. Para obter mais informações, consulte a seção [Observações.](#remarks) Esse parâmetro pode ser `null`.

`lFlags`  
[em] Uma combinação de campos de bits. Para obter mais informações, consulte a seção [Observações.](#remarks)

`pQualifierValue`[em] Um ponteiro para `VARIANT` uma estrutura válida inicializada para um valor de filtro. Esse parâmetro pode ser `null`.

`pstrNames`  
[fora] Uma `SAFEARRAY` estrutura que contém nomes de propriedades. Na entrada, este parâmetro deve ser `null`sempre um ponteiro para . Consulte a seção [Observações](#remarks) para obter mais informações.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve um fracasso geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos ou uma combinação incorreta de sinalizadores e parâmetros foi especificada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::GetNames.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)

Os chamados retornados são controlados por uma combinação de bandeiras e parâmetros. Por exemplo, a função pode retornar os nomes de todas as propriedades ou apenas os nomes das propriedades-chave.  O filtro primário é `lFlags` especificado no parâmetro, e os outros parâmetros variam dependendo dele.

Os valores `lFlags` da bandeira em são campos de bits

As bandeiras que podem `lEnumFlags` ser passadas como argumento são campos de bits definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-las como constantes em seu código.  Você pode combinar uma bandeira de cada grupo com qualquer bandeira de qualquer outro grupo. No entanto, bandeiras do mesmo grupo são mutuamente exclusivas.

| Bandeiras do Grupo 1 |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Devolva todos os nomes das propriedades. `strQualifierName`e `pQualifierVal` não são usados. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Retornar somente propriedades que tenham um qualificador `strQualifierName` do nome especificado pelo parâmetro. Se este sinalizador for usado, você deve especificar `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Retornar apenas propriedades que não possuem um qualificador `strQualifierName` do nome especificado pelo parâmetro. Se este sinalizador for usado, você deve especificar `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Retornar somente propriedades que tenham um qualificador `wszQualifierName` do nome especificado pelo parâmetro e `pQualifierVal` também tenham um valor idêntico ao especificado pela estrutura. Se este sinalizador for usado, `wszQualifierName` você `pQualifierValue`deve especificar a e a . |

| Bandeiras do Grupo 2 |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Devolva apenas os nomes das propriedades que definem as chaves. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Devolva apenas nomes de propriedade que são referências de objeto. |

| Bandeiras do Grupo 3 |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Devolva apenas nomes de propriedades que pertencem à classe mais derivada. Exclua propriedades das classes-mãe. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Devolva apenas nomes de propriedades que pertencem às classes dos pais. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Devolva apenas os nomes das propriedades do sistema. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Devolva apenas os nomes das propriedades não-sistema. |

A função sempre aloca `SAFEARRAY` um `WBEM_S_NO_ERROR`novo `pstrNames` se retornar, e é sempre definida para apontar para ela. A matriz retornada pode ter 0 elementos se nenhuma propriedade corresponder aos filtros especificados. Se a função retornar `WBM_S_NO_ERROR`um valor `SAFEARRAY` diferente, uma nova estrutura não será devolvida.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
