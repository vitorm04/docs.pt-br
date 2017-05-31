---
title: "Mitigação: CspParameters.ParentWindowHandle espera um HWND | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- CspParameters.ParentWindowHandle
- CspParameters.ParentWindowHandle retargeting change
ms.assetid: 33264333-71d6-4d43-8827-9c98878cfea7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: 31898c86adc687b63a1b7f02eee98aae9b16c5f7
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a>Mitigação: CspParameters.ParentWindowHandle espera um HWND

A propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A>, introduzida no .NET Framework 2.0, permite que um aplicativo registre um valor de identificador de janela pai, de modo que qualquer interface do usuário necessária para acessar a chave (por exemplo, uma caixa de diálogo de solicitação de PIN ou de consentimento) seja aberta como um filho modal para a janela especificada. Em aplicativos destinados ao .NET Framework 4.7, um identificador de janela (HWND) pode ser atribuído a essa propriedade.

Nas versões do .NET Framework até o .NET Framework 4.6.2, esperava-se que o valor atribuído à propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> fosse um <xref:System.IntPtr> que representasse o local na memória no qual o valor de HWND residia. No Windows 7 e nas versões anteriores do sistema operacional Windows, definir a propriedade como `form.Handle` não tinha efeito, mas no Windows 8 e nas versões posteriores, isso resulta em uma <xref:System.Security.Cryptography> com a mensagem "O parâmetro está incorreto".

A partir dos aplicativos destinados ao .NET Framework 4.7, um aplicativo do Windows Forms pode definir a propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> com um código semelhante ao seguinte:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a>Impacto

Os aplicativos destinados ao .NET Framework 4.7 ou posterior que desejam registrar um relacionamento de janela pai são incentivados a usar o formulário simplificado:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a>Redução

Os desenvolvedores que identificaram que o valor correto era o endereço do local da memória que mantinha o valor de `form.Handle` podem optar por não aceitar essa alteração de comportamento, definindo a opção de <xref:System.Security.AppContext> `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` para `true`:

- Configurando de forma programática as opções de compatibilidade na instância <xref:System.Security.AppContext>.

- Adicionando a seguinte linha na seção `<runtime>` do arquivo app.config:
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

Por outro lado, os usuários que desejam aceitar o novo comportamento para aplicativos que são executados no .NET Framework 4.7, mas que se destinam a uma versão anterior do .NET Framework, podem definir a opção de <xref:System.Security.AppContext> para `false`.
 
## <a name="see-also"></a>Consulte também

[Alterações de redirecionamento no .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

