---
title: 'Como: Adicionar uma referência de serviço de dados (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790743"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Como: Adicionar uma referência de serviço de dados (WCF Data Services)

Você pode usar a caixa de diálogo **Adicionar referência de serviço** no Visual Studio para adicionar uma referência a WCF Data Services. Isso permite que você acesse mais facilmente um serviço de dados em um aplicativo cliente que você desenvolve no Visual Studio. Quando você concluir este procedimento, as classes de dados serão geradas com base nos metadados obtidos do serviço de dados. Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Adicionar uma referência de serviço de dados

1. Adicional Se o serviço de dados não fizer parte da solução e ainda não estiver em execução, inicie o serviço de dados e anote o URI do serviço de dados.

2. No Visual Studio, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto cliente e selecione **Adicionar** > **referência de serviço**.

3. Se o serviço de dados fizer parte da solução atual, clique em **descobrir**.

     - ou -

     Na caixa de texto **endereço** , digite a URL base do serviço de dados, `http://localhost:1234/Northwind.svc`como e clique em **ir**.

4. Selecione **OK**.

     Um novo arquivo de código que contém as classes de dados que podem acessar e interagir com os recursos do serviço de dados é adicionado ao projeto.

## <a name="see-also"></a>Consulte também

- [Quickstart](quickstart-wcf-data-services.md) (Início rápido)
