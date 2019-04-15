---
title: 'Como: Configurar um domínio do aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe0c7ecf1b0daf0e9ea56ec590083fe1ccd2d693
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225073"
---
# <a name="how-to-configure-an-application-domain"></a>Como: Configurar um domínio do aplicativo
Você pode fornecer o Common Language Runtime com informações de configuração para um novo domínio de aplicativo usando a classe <xref:System.AppDomainSetup>. Ao criar seus próprios domínios de aplicativo, a propriedade mais importante é <xref:System.AppDomainSetup.ApplicationBase%2A>. As outras propriedades **AppDomainSetup** são usadas principalmente por hosts de tempo de execução para configurar um domínio de aplicativo específico.  
  
 A propriedade **ApplicationBase** define o diretório raiz do aplicativo. Quando o tempo de execução precisar atender a uma solicitação de tipo, ele investigará em busca do assembly que contém o tipo no diretório especificado pela propriedade **ApplicationBase**.  
  
> [!NOTE]
>  Um novo domínio de aplicativo herdará apenas a propriedade **ApplicationBase** do criador.  
  
 O exemplo a seguir cria uma instância da classe **AppDomainSetup**, usa essa classe para criar um novo domínio de aplicativo, escreve as informações no console e então descarrega o domínio de aplicativo.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Programação com domínios do aplicativo](application-domains.md#programming-with-application-domains)
- [Usando domínios do aplicativo](../../../docs/framework/app-domains/use.md)
