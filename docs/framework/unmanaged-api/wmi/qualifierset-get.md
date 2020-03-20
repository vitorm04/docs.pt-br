---
title: QualifierSet_Get função (referência de API não gerenciada)
description: A função QualifierSet_Get recebe um qualificador nomeado.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174882"
---
# <a name="qualifierset_get-function"></a>Função QualifierSet_Get
Obtém o qualificador nomeado especificado.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>parâmetros

`vFunc`[em] Este parâmetro não é usado.

`ptr`[em] Um ponteiro para uma instância [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`wszName`[em] O nome do qualificador cujo valor é solicitado.

`lFlags`[em] Reservados. Este parâmetro deve ser 0.

`pVal`[fora] Quando bem sucedido, o tipo e valor corretos para o qualificador. Se a função `VARIANT` falhar, `pVal` o apontado por não é modificado. Se este parâmetro `null`for, o parâmetro é ignorado.

`plFlavor`[fora] Um ponteiro para um LONG que recebe os bits de sabor qualificador para o qualificador solicitado. Se a informação do sabor não for `null`desejada, este parâmetro pode ser .

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | O qualificador especificado não existe. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemQualifierSet::Get.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get)

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
