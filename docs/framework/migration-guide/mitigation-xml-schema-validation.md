---
title: "Mitigação: validação de esquema XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8bc8aab23490b5531a155798520936cacbd6a6d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-xml-schema-validation"></a>Mitigação: validação de esquema XML
No [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], a validação do esquema XSD detectará uma violação da restrição exclusiva se uma chave composta for usada e uma chave estiver vazia.  
  
## <a name="impact"></a>Impacto  
 O impacto dessa alteração deve ser mínimo: com base na especificação do esquema, um erro de validação do esquema será esperado se `xsd:unique` for violado usando uma chave composta com uma chave vazia.  
  
## <a name="mitigation"></a>Redução  
 Se um erro de validação do esquema for detectado se uma chave composta tiver uma chave vazia, é um recurso configurável:  
  
-   Começando com os aplicativos que se destinam ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], a detecção do erro de validação do esquema é habilitada por padrão; no entanto, é possível recusá-la para que o erro de validação do esquema não seja detectado.  
  
-   Em aplicativos que são executado no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], mas se destinam ao [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] e versões anteriores, um erro de validação do esquema não é detectado por padrão; no entanto, é possível aceitá-lo para que o erro de validação do esquema seja detectado.  
  
 Esse comportamento pode ser configurado usando a classe <xref:System.AppContext> para definir o valor da opção `System.Xml.IgnoreEmptyKeySequences`. Como o valor padrão da opção é `false` (sequências de chaves vazias não são ignoradas), os aplicativos que se destinam ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] podem recusar o comportamento usando o seguinte código para definir o valor da opção como `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Para aplicativos que se destinam ao [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] e às versões anteriores, como o valor padrão da opção é `true` (sequências de chaves vazias são ignoradas), é possível garantir que uma chave composta com uma chave vazia gere um erro de validação do esquema usando o código a seguir para definir o valor da opção como `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
