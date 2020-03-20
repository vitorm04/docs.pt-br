---
ms.openlocfilehash: 6fafb689af5d50b31b19f5d1fe7090a6c256ca45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802526"
---
### <a name="wpf-printing-stack-update"></a>Atualização da pilha de impressão do WPF

|   |   |
|---|---|
|Detalhes|Agora, as APIs de Impressão do WPF que usam <xref:System.Printing.PrintQueue?displayProperty=name>chamam a API de Impressão Pacote de Documentos do Windows em vez da API de Impressão XPS, que foi preterida. A alteração foi feita para fins de manutenção. Nem usuários nem os desenvolvedores devem ver todas as alterações no comportamento ou no uso da API. A nova pilha de impressão é habilitada por padrão ao ser executada na Atualização do Windows 10 para Criadores. A pilha de impressão antiga continuará a funcionar como antes nas versões mais antigas do Windows.|
|Sugestão|Para usar a pilha antiga na Atualização do Windows 10 para Criadores, defina o valor REG_DWORD <code>UseXpsOMPrinting</code> da chave do Registro <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> como <code>1</code>.|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Type|Runtime|
