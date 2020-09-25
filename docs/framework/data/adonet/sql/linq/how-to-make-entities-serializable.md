---
title: 'Como: tornar a entidades serializáveis'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: f4528cab21ac678f5d06717d0ce6e7ff7e77d3e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203495"
---
# <a name="how-to-make-entities-serializable"></a>Como: tornar a entidades serializáveis

Você pode fazer entidades serializável quando você gerenciar seu código. Classes de entidade são decoradas com o atributo de <xref:System.Runtime.Serialization.DataContractAttribute> , e colunas com o atributo de <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
 Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para essa finalidade.  
  
 Se você estiver usando a ferramenta de linha de comando SqlMetal, use a opção **/Serialization** com o `unidirectional` argumento. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemplo  

 As seguintes linhas de comando de SQLMetal gerenciar os arquivos que têm entidades serializável.  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Veja também

- [Serialização](serialization.md)
- [Criando o modelo de objeto](creating-the-object-model.md)
