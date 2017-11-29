---
title: "Como: Faça a entidades Serializável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 96d8e05fd6ce71536eacd909a831da0e14aa2f3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-entities-serializable"></a>Como: Faça a entidades Serializável
Você pode fazer entidades serializável quando você gerenciar seu código. Classes de entidade são decoradas com o atributo de <xref:System.Runtime.Serialization.DataContractAttribute> , e colunas com o atributo de <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
 Os desenvolvedores que usam [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] podem usar [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] essa finalidade.  
  
 Se você estiver usando a ferramenta de linha de comando SQLMetal, use o **/serialization** opção com o `unidirectional` argumento. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemplo  
 As seguintes linhas de comando de SQLMetal gerenciar os arquivos que têm entidades serializável.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Consulte também  
 [Serialização](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [Criando o modelo de objeto](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
