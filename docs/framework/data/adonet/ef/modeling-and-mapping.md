---
title: Modelando e mapeando
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 847d518710b21df714343b541401ff7fc8443fb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034015"
---
# <a name="modeling-and-mapping"></a>Modelando e mapeando
No [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], você pode definir o modelo conceitual, o modelo de armazenamento e o mapeamento entre os dois da maneira mais adequada ao seu aplicativo. As ferramentas de modelo de dados de entidade no Visual Studio permitem que você crie um. [arquivo edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) de um banco de dados ou modelo gráfico e atualize esse arquivo quando o banco de dados ou o modelo é alterado.  
  
 A partir do Entity Framework 4.1, você também pode criar um modelo programaticamente usando o desenvolvimento Code First. Há dois cenários diferentes para desenvolvimento Code First. Em ambos os casos, o desenvolvedor define um modelo codificando definições de classe do .NET Framework e, em seguida, opcionalmente especifica o mapeamento adicional ou a configuração usando Anotações de Dados ou a API fluente.  
  
 Para obter mais informações, consulte [criando e mapeando um modelo conceitual](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Você também pode usar o gerador de EDM, que é incluído com o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. O EdmGen.exe gera os arquivos .csdl, .ssdl e .msl de uma fonte de dados existente. Você também pode criar manualmente o modelo e o conteúdo do mapeamento. Para obter mais informações, consulte [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
