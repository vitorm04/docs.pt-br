---
title: "Método IMetaDataImport::FindMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMethod
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b081a5e3668110ea6281c245f507b56ac48b9ab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmethod-method"></a>Método IMetaDataImport::FindMethod
Obtém um ponteiro para o MethodDef token para o método que é incluído por especificado <xref:System.Type> e que tem a assinatura de nome e os metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O `mdTypeDef` token para o tipo (uma classe ou interface) que inclui o membro a ser pesquisado. Se esse valor for `mdTokenNil`, em seguida, a pesquisa é feita para uma função global.  
  
 `szName`  
 [in] O nome do método a ser pesquisado.  
  
 `pvSigBlob`  
 [in] Um ponteiro para a assinatura de metadados de binários do método.  
  
 `cbSigBlob`  
 [in] O tamanho em bytes do `pvSigBlob`.  
  
 `pmb`  
 [out] Um ponteiro para o token MethodDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Especifique o método usando sua classe ou interface de delimitador (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`). Pode haver vários métodos com o mesmo nome em uma classe ou interface. Nesse caso, passe a assinatura do método para encontrar a correspondência exclusiva.  
  
 A assinatura é passado para `FindMethod` deve foram gerados no escopo atual, porque as assinaturas associadas a um determinado escopo. Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador. O token é um índice na tabela de TypeDef local. Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMethod`.  
  
 `FindMethod`localiza apenas os métodos que foram definidos diretamente na classe ou interface. métodos herdados não for encontrada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.MethodInfo>  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
