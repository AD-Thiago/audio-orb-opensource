# 🤝 Guia de Contribuição - Audio Orb

Obrigado por considerar contribuir para o Audio Orb! Este documento fornece diretrizes para tornar sua contribuição útil e eficaz.

## 📝 Índice

- [Código de Conduta](#código-de-conduta)
- [Como Posso Contribuir?](#como-posso-contribuir)
- [Processo de Desenvolvimento](#processo-de-desenvolvimento)
- [Padrões de Código](#padrões-de-código)
- [Processo de Pull Request](#processo-de-pull-request)
- [Reportando Bugs](#reportando-bugs)
- [Sugerindo Melhorias](#sugerindo-melhorias)

## 📜 Código de Conduta

Este projeto e todos os participantes são regidos por um código de conduta. Ao participar, você concorda em manter este código. Por favor, relate comportamentos inaceitáveis abrindo uma issue.

### Nossos Compromissos

- Usar linguagem acolhedora e inclusiva
- Respeitar pontos de vista e experiências diferentes
- Aceitar críticas construtivas com graça
- Focar no que é melhor para a comunidade
- Mostrar empatia com outros membros da comunidade

## 🚀 Como Posso Contribuir?

### 🐛 Reportando Bugs

Bugs são rastreados como issues do GitHub. Antes de criar uma issue de bug:

1. **Verifique se o bug já foi reportado** pesquisando nas issues existentes
2. **Verifique se o bug foi corrigido** tentando reproduzi-lo na branch `main`
3. **Isole o problema** para facilitar a reprodução

Quando criar uma issue de bug, inclua:

- **Título claro e descritivo**
- **Passos exatos para reproduzir o problema**
- **Comportamento esperado vs. comportamento observado**
- **Capturas de tela** (se aplicável)
- **Ambiente**:
  - Versão do Node.js
  - Sistema operacional
  - Navegador e versão
  - Versão do Audio Orb
- **Informações adicionais** relevantes

### ✨ Sugerindo Melhorias

Sugestões de melhorias também são rastreadas como issues do GitHub. Ao criar uma sugestão de melhoria, inclua:

- **Título claro e descritivo**
- **Descrição detalhada da melhoria sugerida**
- **Explique por que esta melhoria seria útil** para a maioria dos usuários
- **Liste alguns exemplos** de como a melhoria funcionaria
- **Mencione outros projetos** onde esta melhoria existe, se aplicável

### 📝 Melhorando a Documentação

Boa documentação é crucial! Você pode ajudar:

- Corrigindo erros de digitação ou gramática
- Melhorando a clareza das explicações
- Adicionando exemplos ou tutoriais
- Traduzindo documentação para outros idiomas
- Criando guias de usuário ou vídeos tutoriais

### 🎤 Adicionando Novos Motores TTS

Uma das melhores maneiras de contribuir é adicionar suporte para novos motores TTS:

1. Crie um novo arquivo em `src/engines/`
2. Implemente a interface `TTSEngine`:

```typescript
interface TTSEngine {
  name: string;
  synthesize(text: string, voice: string): Promise<AudioBuffer>;
  listVoices(): Promise<Voice[]>;
  initialize?(): Promise<void>;
  cleanup?(): Promise<void>;
}
```

3. Adicione testes para seu novo motor
4. Atualize a documentação
5. Adicione exemplos de uso

### 🎨 Melhorando Visualizações

Contribuições para melhorar os efeitos visuais 3D são bem-vindas:

- Novos efeitos de visualização de áudio
- Otimizações de performance
- Opções de personalização
- Modos de visualização alternativos

## 🛠️ Processo de Desenvolvimento

### Configuração do Ambiente

1. **Fork o repositório** no GitHub
2. **Clone seu fork** localmente:
   ```bash
   git clone https://github.com/SEU_USUARIO/audio-orb-opensource.git
   cd audio-orb-opensource
   ```

3. **Adicione o repositório upstream**:
   ```bash
   git remote add upstream https://github.com/AD-Thiago/audio-orb-opensource.git
   ```

4. **Instale as dependências**:
   ```bash
   npm install
   ```

5. **Configure variáveis de ambiente**:
   ```bash
   cp .env.example .env
   # Edite o .env com suas chaves de API
   ```

### Workflow de Desenvolvimento

1. **Crie uma branch para sua feature**:
   ```bash
   git checkout -b feature/minha-nova-feature
   ```

2. **Faça suas alterações**:
   - Escreva código limpo e bem documentado
   - Siga os padrões de código do projeto
   - Adicione testes quando aplicável

3. **Teste suas alterações**:
   ```bash
   npm run dev      # Servidor de desenvolvimento
   npm run test     # Execute testes
   npm run lint     # Verificação de lint
   npm run build    # Build de produção
   ```

4. **Commit suas alterações**:
   ```bash
   git add .
   git commit -m "feat: adicionar suporte para novo motor TTS"
   ```

5. **Mantenha sua branch atualizada**:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

6. **Push para seu fork**:
   ```bash
   git push origin feature/minha-nova-feature
   ```

## ⚙️ Padrões de Código

### Estilo de Código

- **TypeScript**: Use TypeScript para todo o código novo
- **ESLint**: Siga as regras do ESLint configuradas no projeto
- **Prettier**: Formate o código com Prettier antes de commitar
- **Naming Conventions**:
  - `camelCase` para variáveis e funções
  - `PascalCase` para classes e interfaces
  - `UPPER_CASE` para constantes

### Mensagens de Commit

Siga o padrão [Conventional Commits](https://www.conventionalcommits.org/):

```
<tipo>(<escopo>): <descrição>

[corpo opcional]

[rodapé opcional]
```

**Tipos**:
- `feat`: Nova funcionalidade
- `fix`: Correção de bug
- `docs`: Alterações na documentação
- `style`: Formatação, ponto e vírgula faltando, etc.
- `refactor`: Refatoração de código
- `perf`: Melhorias de performance
- `test`: Adição ou correção de testes
- `chore`: Manutenção, atualização de dependências

**Exemplos**:
```bash
feat(xtts): adicionar suporte para clonagem de voz
fix(audio): corrigir vazamento de memória no processador de áudio
docs(readme): atualizar instruções de instalação
```

### Testes

- Escreva testes para novas funcionalidades
- Mantenha a cobertura de testes acima de 80%
- Use testes unitários para lógica de negócio
- Use testes de integração para fluxos completos

```typescript
// Exemplo de teste
describe('TTSEngine', () => {
  it('deve sintetizar áudio a partir de texto', async () => {
    const engine = new MeuMotorTTS();
    const audio = await engine.synthesize('Olá mundo', 'voz-padrao');
    expect(audio).toBeInstanceOf(AudioBuffer);
  });
});
```

### Documentação de Código

Use JSDoc para documentar funções e classes:

```typescript
/**
 * Sintetiza áudio a partir de texto usando o motor TTS especificado.
 * 
 * @param text - O texto para sintetizar
 * @param voice - O identificador da voz a usar
 * @param options - Opções adicionais de síntese
 * @returns Promise que resolve para um AudioBuffer
 * @throws {TTSError} Se a síntese falhar
 * 
 * @example
 * ```typescript
 * const audio = await synthesize('Olá', 'pt-BR-voz1');
 * ```
 */
async synthesize(
  text: string,
  voice: string,
  options?: SynthesisOptions
): Promise<AudioBuffer>
```

## 🔄 Processo de Pull Request

1. **Certifique-se de que seu código segue os padrões**:
   - Todos os testes passam
   - Lint sem erros
   - Build com sucesso

2. **Atualize a documentação**:
   - README.md se adicionar novas funcionalidades
   - Comentários no código
   - CHANGELOG.md

3. **Crie o Pull Request**:
   - Use um título claro e descritivo
   - Descreva as alterações feitas
   - Referencie issues relacionadas
   - Inclua screenshots para mudanças visuais

4. **Template de Pull Request**:

```markdown
## Descrição
Descreva brevemente as alterações propostas.

## Tipo de Mudança
- [ ] Bug fix (alteração não-breaking que corrige uma issue)
- [ ] Nova feature (alteração não-breaking que adiciona funcionalidade)
- [ ] Breaking change (fix ou feature que causaria funcionalidade existente não funcionar como esperado)
- [ ] Documentação

## Como Foi Testado?
Descreva os testes que você executou.

## Checklist
- [ ] Meu código segue o guia de estilo do projeto
- [ ] Fiz uma auto-revisão do meu código
- [ ] Comentei meu código, particularmente em áreas difíceis
- [ ] Fiz alterações correspondentes na documentação
- [ ] Minhas alterações não geram novos avisos
- [ ] Adicionei testes que provam que minha correção é eficaz ou que minha feature funciona
- [ ] Testes unitários novos e existentes passam localmente
```

5. **Processo de Revisão**:
   - Aguarde revisão dos mantenedores
   - Responda aos comentários e feedbacks
   - Faça alterações solicitadas
   - Seja paciente e respeitoso

## 🎯 Prioridades de Desenvolvimento

### Alta Prioridade
- Correções de bugs críticos
- Melhorias de segurança
- Melhorias de performance
- Suporte a novos motores TTS

### Média Prioridade
- Novas features solicitadas pela comunidade
- Melhorias na documentação
- Otimizações de código
- Melhorias de UI/UX

### Baixa Prioridade
- Refatorações não essenciais
- Features experimentais
- Melhorias cosméticas

## 💬 Comunicação

- **GitHub Issues**: Para bugs, features e discussões
- **Pull Requests**: Para revisão de código
- **Discord** (em breve): Para discussões em tempo real

## 📚 Recursos Adicionais

- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [WebGL Fundamentals](https://webglfundamentals.org/)
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
- [Conventional Commits](https://www.conventionalcommits.org/)

## ❓ Perguntas?

Se tiver alguma dúvida sobre como contribuir:

1. Verifique a documentação existente
2. Procure em issues fechadas
3. Abra uma nova issue com sua pergunta

---

**Obrigado por contribuir para o Audio Orb! 🎉**

Cada contribuição, não importa quão pequena, ajuda a tornar o Audio Orb melhor para todos.
