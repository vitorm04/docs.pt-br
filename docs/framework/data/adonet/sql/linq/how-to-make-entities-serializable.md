---
title: 'Como: Faça a entidades Serializável'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: c3b877df9707e0f98dbc2238d910842649def07f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-entities-serializable"></a>Como: Faça a entidades Serializável
Você pode fazer entidades serializável quando você gerenciar seu código. Classes de entidade são decoradas com o atributo de <xref:System.Runtime.Serialization.DataContractAttribute> , e colunas com o atributo de <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
 Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para essa finalidade.  
  
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
