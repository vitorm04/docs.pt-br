---
title: 'Como: Tornar entidades serializáveis'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 9b4ff81b4a779b474097de1a69e65f4864e08691
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604200"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="c382d-102">Como: Tornar entidades serializáveis</span><span class="sxs-lookup"><span data-stu-id="c382d-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="c382d-103">Você pode fazer entidades serializável quando você gerenciar seu código.</span><span class="sxs-lookup"><span data-stu-id="c382d-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="c382d-104">Classes de entidade são decoradas com o atributo de <xref:System.Runtime.Serialization.DataContractAttribute> , e colunas com o atributo de <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c382d-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="c382d-105">Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="c382d-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="c382d-106">Se você estiver usando a ferramenta de linha de comando SQLMetal, use o **/serialization** a opção com o `unidirectional` argumento.</span><span class="sxs-lookup"><span data-stu-id="c382d-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="c382d-107">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c382d-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c382d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c382d-108">Example</span></span>  
 <span data-ttu-id="c382d-109">As seguintes linhas de comando de SQLMetal gerenciar os arquivos que têm entidades serializável.</span><span class="sxs-lookup"><span data-stu-id="c382d-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="c382d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c382d-110">See also</span></span>
- [<span data-ttu-id="c382d-111">Serialização</span><span class="sxs-lookup"><span data-stu-id="c382d-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="c382d-112">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="c382d-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
