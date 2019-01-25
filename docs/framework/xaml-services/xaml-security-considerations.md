---
title: Considerações sobre segurança XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 6cd09295f9dac26011652d6b0a33318841b04072
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648356"
---
# <a name="xaml-security-considerations"></a>Considerações sobre segurança XAML
Este tópico descreve as práticas recomendadas de segurança em aplicativos quando você usa XAML e a API de serviços XAML do .NET Framework.  
  
## <a name="untrusted-xaml-in-applications"></a>XAML não confiável em aplicativos  
 No sentido mais geral, o XAML não confiável é qualquer fonte XAML que seu aplicativo não especificamente incluem ou emitir.  
  
 XAML que é compilado em ou armazenado como um `resx`-tipo de recurso em um assembly assinado e não confiáveis não é inerentemente não confiável. Você pode confiar a XAML tanto quanto você confia no assembly como um todo. Na maioria dos casos, você só estiver preocupado com os aspectos de confiança do XAML flexível, que é uma fonte XAML carregados a partir de um fluxo ou outras e/s. XAML flexível não é um componente específico ou recurso de um modelo de aplicativo com uma infraestrutura de empacotamento e implantação. No entanto, um assembly pode implementar um comportamento que envolve o carregamento de XAML flexível.  
  
 Para o XAML não confiável, você deve tratá-lo geralmente o mesmo como se fosse o código não confiável. Usar área restrita ou outras metáforas para impedir que o XAML possivelmente não confiável acessem seu código confiável.  
  
 A natureza dos recursos XAML dá o XAML o direito de construir objetos e defina suas propriedades. Esses recursos também incluem o acesso a conversores de tipo de mapeamento e acessando assemblies no domínio do aplicativo, usando as extensões de marcação, `x:Code` blocos e assim por diante.  
  
 Além de seus recursos de nível de linguagem XAML é usado para a definição de interface do usuário em muitas tecnologias. Carregar XAML não confiável pode significar a carregamento de uma interface do usuário mal-intencionado falsificação.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Compartilhamento de contexto entre leitores e gravadores  
 A arquitetura de serviços de XAML do .NET Framework para leitores XAML e gravadores XAML geralmente requer o compartilhamento de um leitor XAML para um gravador XAML ou um contexto de esquema XAML compartilhado. Compartilhando objetos ou contextos pode ser necessária se você estiver escrevendo uma lógica de loop de nó XAML ou fornecendo um personalizado salvar caminho. Você não deve compartilhar instâncias do leitor XAML, contexto de esquema XAML não padrão ou as configurações para as classes de leitor/gravador XAML entre o código não confiável e não confiáveis.  
  
 A maioria dos cenários e as operações que envolvem o objeto XAML escrevendo para um tipo de CLR fazendo poderá usar o contexto de esquema XAML padrão. O contexto do esquema XAML padrão não incluir explicitamente as configurações que poderiam comprometer a confiança total. Portanto, é seguro compartilhar contexto entre confiáveis e componentes de leitor/gravador XAML. No entanto, se você fizer isso, ele ainda é uma prática recomendada manter tais leitores e gravadores em separado <xref:System.AppDomain> escopos, com um deles especificamente pretendido/área restrita de confiança parcial.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>Namespaces XAML e a confiança do Assembly  
 A sintaxe básica de não-qualificado e a definição para como XAML interpreta um mapeamento de namespace XAML personalizado a um assembly não faz distinção entre um assembly confiável e como carregado no domínio de aplicativo. Portanto, é tecnicamente possível que um assembly não confiável falsificar o mapeamento de namespace XAML desejado de um assembly confiável e capturar informações de propriedade e o objeto declarado de uma fonte XAML. Se você tiver requisitos de segurança para evitar essa situação, o mapeamento de namespace XAML pretendido deve ser feito usando uma das seguintes técnicas:  
  
-   Use um nome totalmente qualificado do assembly com nome forte em qualquer mapeamento de namespace XAML feito pelo XAML do seu aplicativo.  
  
-   Restringir o assembly mapeando para um conjunto fixo de assemblies de referência, com a construção de um determinado <xref:System.Xaml.XamlSchemaContext> para seu XAML leitores e XAML do objeto gravadores. Consulte <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>Mapeamento de tipo XAML e o tipo de acesso de sistema  
 XAML dá suporte a seu próprio sistema de tipo, que é um par para como o CLR implementa o sistema de tipo CLR básico de várias maneiras. No entanto, para determinados aspectos de reconhecimento de tipo no qual você está tomando decisões de confiança sobre um tipo com base em suas informações de tipo, você deve adiar as informações de tipo no CLR, tipos de suporte. Isso ocorre porque alguns dos recursos de relatório específicos do sistema de tipo XAML são deixadas abertas como métodos virtuais e, portanto, não são totalmente sob o controle das implementações de serviços de XAML do .NET Framework do originais. Esses pontos de extensibilidade existem porque o sistema de tipo XAML é extensível, para corresponder a extensibilidade do XAML em si e suas possíveis estratégias alternativas de mapeamento de tipo versus a implementação do padrão baseado em CLR e o contexto de esquema XAML padrão. Para obter mais informações, consulte as notas específicas em diversas propriedades de <xref:System.Xaml.XamlType> e <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Xaml.Permissions.XamlAccessLevel>
