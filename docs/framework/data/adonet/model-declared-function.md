---
title: "função declarada por modelo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 85fb07b3577e7e61536664a346154ba9602cd9f3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="model-declared-function"></a>função declarada por modelo
Um *função declarada por modelo* é uma função que é declarada em um modelo conceitual, mas não está definida no modelo conceitual. A função pode ser definida no ambiente de hospedagem ou de armazenamento. Por exemplo, uma função o declarada pode ser mapeada para uma função que está definida em uma base de dados, bem expõe a funcionalidade do lado do modelo conceitual.  
  
 A declaração de uma função declarada modelo contém as informações a seguir:  
  
-   O nome da função. (Necessário)  
  
-   O tipo do valor de retorno. (Opcional)  
  
    > [!NOTE]
    >  Se nenhum valor de retorno for especificado, o tipo de retorno é vago.  
  
-   Informações de parâmetro, incluindo o nome do parâmetro e o tipo. (Opcional)  
  
## <a name="example"></a>Exemplo  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. No CSDL, uma implementação de uma função declarada por modelo é um [importação de função](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d). CSDL seguir define um contêiner de entidade com uma definição de importação de função. Observe que o tipo de retorno da função é vago desde que nenhum tipo de retorno é especificado.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
