---
title: 'Como: tornar a entidades serializáveis'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: fd687ba5dce16baee063f1d3bb9521c6664988b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743281"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="6ff70-102">Como: tornar a entidades serializáveis</span><span class="sxs-lookup"><span data-stu-id="6ff70-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="6ff70-103">Você pode fazer entidades serializável quando você gerenciar seu código.</span><span class="sxs-lookup"><span data-stu-id="6ff70-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="6ff70-104">Classes de entidade são decoradas com o atributo de <xref:System.Runtime.Serialization.DataContractAttribute> , e colunas com o atributo de <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="6ff70-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="6ff70-105">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="6ff70-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="6ff70-106">Se você estiver usando a ferramenta de linha de comando SQLMetal, use o **/serialization** a opção com o `unidirectional` argumento.</span><span class="sxs-lookup"><span data-stu-id="6ff70-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="6ff70-107">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6ff70-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff70-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ff70-108">Example</span></span>  
 <span data-ttu-id="6ff70-109">As seguintes linhas de comando de SQLMetal gerenciar os arquivos que têm entidades serializável.</span><span class="sxs-lookup"><span data-stu-id="6ff70-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ff70-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ff70-110">See also</span></span>

- [<span data-ttu-id="6ff70-111">Serialização</span><span class="sxs-lookup"><span data-stu-id="6ff70-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="6ff70-112">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="6ff70-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
