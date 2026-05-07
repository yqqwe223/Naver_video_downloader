# Naver Media Analyzer (Analisador de Mídia Naver)

> 🔍 Uma ferramenta frontend leve para fins educacionais e de pesquisa, suportando extração de metadados de conteúdo publicamente acessível no Naver

🌐 Demonstração online: [https://twittervideodownloaderx.com/naver_downloader_po](https://twittervideodownloaderx.com/naver_downloader_po)

---

## 📋 Visão Geral do Projeto

Este projeto foi desenvolvido para fins educacionais e de pesquisa técnica. Trata-se de um utilitário frontend leve projetado para ajudar desenvolvedores e estudantes a compreender como extrair metadados estruturados de páginas públicas do Naver (Naver Blog, Naver TV, Naver Post, etc.), utilizando interfaces de visualização web padrão e APIs de dados estruturados.

> 🎯 Casos de uso recomendados:
> - Organização de materiais de estudo pessoais e coleta de ideias
> - Prática de desenvolvimento frontend e pesquisa sobre extração de dados web
> - Aprendizado sobre estruturas de metadados multimídia
> - Arquivamento de conteúdo publicamente acessível com permissão explícita dos detentores de direitos autorais

⚠️ **Aviso importante**: Esta ferramenta funciona exclusivamente com **conteúdo publicamente acessível**. Não oferece suporte e não se destina ao acesso a conteúdo privado, conteúdo que exija login ou qualquer conteúdo com restrições de acesso.

---

## ✨ Principais Funcionalidades

- 🔗 **Reconhecimento Inteligente de Links Públicos**: Detecta automaticamente formatos de URL de conteúdo público do Naver (blog.naver.com, tv.naver.com, post.naver.com, etc.)
- 🎬 **Suporte a Múltiplos Tipos de Recursos**: Extrai metadados para vídeos, imagens, áudios e outros arquivos de mídia publicamente acessíveis (o conteúdo deve estar configurado com visibilidade pública)
- 📐 **Exibição de Informações Básicas**: Mostra tipo de mídia, tamanho do arquivo, timestamp de upload, informações do autor e outros metadados publicamente disponíveis
- 📱 **Design Totalmente Responsivo**: Experiência de usuário otimizada para desktop, tablet e dispositivos móveis
- ⚡ **Arquitetura Priorizando o Lado do Cliente**: A lógica principal de análise é executada no navegador, reduzindo a dependência do servidor e melhorando a velocidade de resposta
- 🔐 **Design Respeitoso com a Privacidade**: Não registra URLs enviadas, não armazena resultados de análise nem coleta quaisquer dados pessoais ou informações de conta do usuário

---

## 🚀 Guia de Início Rápido

1. Abra a plataforma Naver (versão web ou aplicativo) e localize o **conteúdo público** que deseja consultar
2. Copie a URL da página da barra de endereços do navegador (exemplo: `https://blog.naver.com/username/123456789` ou `https://tv.naver.com/v/12345678`)
3. Cole o link no campo de entrada desta ferramenta e clique no botão "Analisar"
4. O sistema extrairá os metadados publicamente disponíveis e exibirá as informações dos recursos acessíveis
5. Selecione o recurso preferido, clique com o botão direito no link e escolha "Salvar link como..." para fazer o download localmente

> 💡 Dicas de uso:
> - Sempre verifique se o conteúdo alvo está configurado com visibilidade "Pública"
> - Se a análise falhar, tente atualizar a página ou verificar sua conexão de rede
> - Para fins de aprendizado, considere usar as Ferramentas do Desenvolvedor do navegador (F12 → Network → Fetch/XHR) junto com esta ferramenta

---

## ⚠️ Conformidade e Isenção de Responsabilidade (Leia com Atenção)

Este projeto opera sob os princípios de "neutralidade técnica" e "conformidade legal". Por favor, revise e aceite o seguinte antes de usar:

### ✅ Práticas Recomendadas
- Analise apenas **conteúdo publicamente acessível** ao qual você tenha acesso legítimo
- Utilize os recursos extraídos estritamente para **aprendizado pessoal, pesquisa ou referência privada**
- Obtenha permissão escrita explícita dos detentores de direitos autorais antes de redistribuir, criar obras derivadas ou usar para fins comerciais
- Sempre credite os criadores originais e indique claramente a atribuição da fonte em seus projetos

### ❌ Atividades Proibidas
- Tentar acessar ou analisar conteúdo privado, conteúdo que exija autenticação ou recursos com restrições de acesso
- Usar esta ferramenta para scraping comercial, serviços de agregação de dados ou geração de receita publicitária
- Enviar solicitações automatizadas de alta frequência, tráfego de bot ou qualquer atividade que possa interromper os serviços do Naver
- Remover, alterar ou ocultar marcas d'água, avisos de direitos autorais ou metadados incorporados
- Usar esta ferramenta para acessar, distribuir ou propagar conteúdo que viole privacidade, leis ou direitos de propriedade intelectual

> 📜 Aviso Legal:
> O uso desta ferramenta deve estar em conformidade com as leis de direitos autorais aplicáveis, regulamentos de proteção de dados, bem como os [Termos de Serviço](https://terms.naver.com/termOfService.naver) e [Política de Privacidade](https://terms.naver.com/privacy.naver) do Naver.
> Os desenvolvedores não assumem responsabilidade por quaisquer problemas legais, danos ou perdas decorrentes do uso indevido desta ferramenta por usuários finais.

---

## 🛠 Notas de Implementação Técnica (Para Desenvolvedores)

> Usuários gerais podem pular esta seção

### Visão Geral da Arquitetura
```
Navegador do Usuário → Módulo de Análise Client-Side → Página Pública do Naver / Interface OEmbed → Extração de Dados Estruturados → Renderização de Resultados
```

### Abordagens Técnicas Principais
- Utiliza a API `fetch` com configuração apropriada de proxy CORS para recuperar metadados de páginas públicas
- Analisa tags Open Graph (`og:video`, `og:image`, `og:title`, etc.) para descoberta de links de recursos
- Aproveita dados estruturados (JSON-LD / Microdata) das páginas de visualização para complementar informações de mídia
- Implementa validação dupla via padrões regex + parsing DOM para reconhecimento robusto de links

### Guia de Auto-hospedagem (Referência)
```bash
# 1. Clonar o repositório (exemplo)
git clone https://github.com/yourname/naver-downloader-po.git

# 2. Implantar arquivos estáticos (HTTPS fortemente recomendado)
#    - Vercel / Netlify / Cloudflare Pages (configuração simples, recomendado)
#    - Nginx + certificado Let's Encrypt (opção de auto-hospedagem)

# 3. Exemplo de configuração de cabeçalhos de segurança (Nginx)
add_header Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline';";
add_header X-Content-Type-Options "nosniff";
add_header Referrer-Policy "strict-origin-when-cross-origin";
add_header X-Frame-Options "DENY";
```

> 🔐 Melhores Práticas para Implantação em Produção:
> - Sempre habilite HTTPS para prevenir ataques man-in-the-middle
> - Implemente limitação de taxa (rate limiting) para prevenir abusos e solicitações excessivas
> - Evite expor lógica de análise sensível que possa ser mal utilizada
> - Revise e atualize regularmente as dependências para aplicar patches de segurança

---

## 🤝 Como Contribuir

Acolhemos contribuições da comunidade para ajudar a melhorar este projeto educacional!

| Tipo de Contribuição | Exemplos |
|---------------------|----------|
| 🐛 Relatórios de Bugs | Envie Issues com etapas detalhadas: URL + informações do navegador + etapas de reprodução |
| 💡 Sugestões de Funcionalidades | Compartilhe ideias construtivas para melhorias de UX, acessibilidade ou novos recursos educacionais |
| 🌍 Ajuda com Traduções | Auxilie na tradução do texto da interface para idiomas adicionais |
| 📚 Documentação | Adicione exemplos de uso, diagramas técnicos ou guias de conformidade |

> Este projeto é lançado sob a [Licença MIT](./LICENSE). Incentivamos o uso livre e modificação para fins educacionais e de pesquisa. Para consultas sobre personalização comercial, entre em contato conosco através de canais separados.

---

## ❓ Perguntas Frequentes (FAQ)

**P: Por que aparece a mensagem "Não foi possível obter o conteúdo"?**  
R: Possíveis razões: ① O link aponta para conteúdo privado ou que exige autenticação ② O conteúdo foi excluído ou configurado como "Apenas para membros" ③ O Naver alterou temporariamente a estrutura da página ④ Restrições de rede ou problemas de CORS. Solução: Verifique o status público → Teste com uma rede diferente → Aguarde e tente novamente.

**P: O vídeo/imagem baixado contém marca d'água?**  
R: Esta ferramenta retorna as URLs de recursos originais fornecidas pela infraestrutura oficial do Naver. A presença de marcas d'água depende inteiramente das configurações de quem fez o upload. Esta ferramenta não adiciona, remove ou modifica quaisquer marcas d'água ou marcas incorporadas.

**P: O processamento em lote para histórico de conteúdo do Naver Blog/TV é suportado?**  
R: A versão atual foca na análise de conteúdo único para priorizar estabilidade e conformidade. Para operações em lote, certifique-se primeiro de que seu caso de uso está alinhado com os [Termos de Serviço](https://terms.naver.com/termOfService.naver) do Naver em relação a limites de taxa e uso de dados.

**P: Esta ferramenta coleta meus dados de uso ou informações da conta do Naver?**  
R: Não. Este é um projeto frontend estático puro sem logging de backend, scripts de analytics, rastreamento baseado em cookies ou vinculação de conta. Todo o processamento ocorre localmente dentro da sua sessão do navegador, e nenhum login é necessário.

**P: É possível analisar postagens privadas do Naver Cafe ou conteúdo de conversas pessoais?**  
R: Não. Esta ferramenta suporta exclusivamente **links de páginas públicas**. A análise de postagens privadas, conteúdo interno do Cafe ou recursos que exijam login não é tecnicamente suportada e é eticamente desencorajada. Isso reflete nosso compromisso fundamental com a privacidade do usuário e conformidade do produto.

---

## 🌱 Nossa Filosofia

> A tecnologia em si é neutra. O que importa é a *intenção* e a *responsabilidade* de quem a utiliza.

Incentivamos desenvolvedores e usuários a abraçar estes valores:

- 🔬 Buscar uma compreensão mais profunda das tecnologias web através da curiosidade e aprendizado ético
- 🤲 Respeitar os direitos dos criadores e a privacidade dos usuários, atribuindo corretamente as fontes e solicitando permissões
- 🌍 Contribuir para um ecossistema digital saudável que equilibre inovação com preservação cultural
- ⚖️ Manter o equilíbrio entre exploração técnica e conformidade legal, praticando desenvolvimento responsável

Juntos, promovamos um ciclo positivo de criação, compartilhamento e uso responsável da tecnologia ✨

---

## 📄 Licença

Este projeto é distribuído sob a [Licença MIT](./LICENSE).

```
Copyright (c) 2026 Naver Media Analyzer Project

É concedida permissão, gratuitamente, a qualquer pessoa que obtenha uma cópia
deste software e dos arquivos de documentação associados (o "Software"), para lidar
no Software sem restrição, incluindo, sem limitação, os direitos
de usar, copiar, modificar, mesclar, publicar, distribuir, sublicenciar e/ou vender
cópias do Software, e permitir que as pessoas a quem o Software é
fornecido façam o mesmo, sujeito às seguintes condições:

O aviso de direitos autorais acima e este aviso de permissão devem ser incluídos em todas
as cópias ou partes substanciais do Software.

O SOFTWARE É FORNECIDO "COMO ESTÁ", SEM GARANTIA DE QUALQUER TIPO, EXPRESSA OU
IMPLÍCITA, INCLUINDO, MAS NÃO SE LIMITANDO ÀS GARANTIAS DE COMERCIABILIDADE,
ADEQUAÇÃO A UM PROPÓSITO ESPECÍFICO E NÃO VIOLAÇÃO. EM NENHUM CASO OS
AUTORES OU DETENTORES DOS DIREITOS AUTORAIS SERÃO RESPONSÁVEIS POR QUALQUER REIVINDICAÇÃO,
DANOS OU OUTRA RESPONSABILIDADE, SEJA EM UMA AÇÃO DE CONTRATO, ATO ILÍCITO
OU DE OUTRA FORMA, DECORRENTE DE, FORA DE OU EM CONEXÃO COM O SOFTWARE
OU O USO OU OUTRAS NEGOCIAÇÕES NO SOFTWARE.
```

---

*📅 Última Atualização: Maio de 2026*  
*🔖 Versão: v1.2.0-po (Otimização frontend / Documentação de conformidade aprimorada / Proteção de privacidade reforçada)*