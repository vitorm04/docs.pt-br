---
title: 'Como: Adicionar uma referência de serviço de dados (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 8bf623ec74c3bd165f63f60e883bfcb532d6900b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633955"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Como: Adicionar uma referência de serviço de dados (WCF Data Services)

Você pode usar o **adicionar referência de serviço** caixa de diálogo no Visual Studio para adicionar uma referência para o WCF Data Services. Isso permite que você acesse mais facilmente um serviço de dados em um aplicativo cliente que você desenvolve no Visual Studio. Quando você concluir este procedimento, as classes de dados são geradas com base nos metadados que é obtido do serviço de dados. Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Adicionar uma referência de serviço de dados

1. (Opcional) Se o serviço de dados não é parte da solução e não já está em execução, inicie o serviço de dados e observe o URI do serviço de dados.

2. No Visual Studio, no **Gerenciador de soluções**, o projeto de cliente com o botão direito e, em seguida, selecione **Add** > **referência de serviço**.

3. Se o serviço de dados é parte da solução atual, clique em **Discover**.

     - ou -

     No **endereço** caixa de texto, digite a URL base do serviço de dados, como `http://localhost:1234/Northwind.svc`e, em seguida, clique em **vá**.

4. Selecione **OK**.

     Um novo arquivo de código que contém as classes de dados que podem acessar e interagir com os recursos do serviço de dados é adicionado ao projeto.

## <a name="see-also"></a>Consulte também

- [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)
