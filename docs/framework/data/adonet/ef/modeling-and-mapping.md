---
title: Modelando e mapeando
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 81080c416fd18c51be6626cb70a23073e049051d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705417"
---
# <a name="modeling-and-mapping"></a>Modelando e mapeando
No [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], você pode definir o modelo conceitual, o modelo de armazenamento e o mapeamento entre os dois da maneira mais adequada ao seu aplicativo. As ferramentas de modelo de dados de entidade no Visual Studio permitem que você crie um. [arquivo edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) de um banco de dados ou modelo gráfico e atualize esse arquivo quando o banco de dados ou o modelo é alterado.  
  
 A partir do Entity Framework 4.1, você também pode criar um modelo programaticamente usando o desenvolvimento Code First. Há dois cenários diferentes para desenvolvimento Code First. Em ambos os casos, o desenvolvedor define um modelo codificando definições de classe do .NET Framework e, em seguida, opcionalmente especifica o mapeamento adicional ou a configuração usando Anotações de Dados ou a API fluente.  
  
 Para obter mais informações, consulte [criando e mapeando um modelo conceitual](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Você também pode usar o gerador de EDM, que é incluído com o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. O EdmGen.exe gera os arquivos .csdl, .ssdl e .msl de uma fonte de dados existente. Você também pode criar manualmente o modelo e o conteúdo do mapeamento. Para obter mais informações, consulte [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
