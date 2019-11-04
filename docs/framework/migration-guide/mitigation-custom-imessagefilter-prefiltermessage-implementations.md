---
title: 'Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457933"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage

Em aplicativos do Windows Forms direcionados a versões do .NET Framework começando com o .NET Framework 4.6.1, uma implementação de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personalizada pode filtrar mensagens quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> for chamado se a implementação <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>:

- Executa uma ou ambas as ações:

  - Adiciona um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.

  - Remove um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. método.

- **E** bombeia mensagens chamando o método <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.

## <a name="impact"></a>Impacto

Essa alteração afeta somente os aplicativos do Windows Forms que se destinam a versões do .NET Framework, começando pelo .NET Framework 4.6.1.

Para aplicativos do Windows Forms direcionados a versões anteriores do .NET Framework, essas implementações podem, em alguns casos, lançar uma exceção <xref:System.IndexOutOfRangeException> quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> é chamado

## <a name="mitigation"></a>Redução

Se essa alteração for indesejável, aplicativos que se destinarem ao .NET Framework 4.6.1 ou a uma versão posterior poderão recusá-la adicionando a seguinte definição de configuração à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Além disso, os aplicativos destinados a versões anteriores do .NET Framework, mas que estão sendo executados no .NET Framework 4.6.1 ou em uma versão posterior, podem aceitar esse comportamento adicionando a seguinte definição de configuração à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Consulte também

- [Compatibilidade de aplicativos](application-compatibility.md)
