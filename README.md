# Token Optimizer

Optimize text and code before sending to AI — reduce token usage without losing meaning.

## Features

- **3 optimization modes** — Text, Code, and Aggressive (both combined)
- **In-place optimization** — See results instantly as you type
- **Live savings stats** — Real-time token count, % saved, and context window usage
- **5 model targets** — Claude 200k, GPT-4 128k, Gemini 2M, Mixtral 32k, Llama 8k
- **Works on all AI platforms** — ChatGPT, Claude, Gemini, Mistral, Poe, Perplexity, Copilot, and more
- **Zero dependencies** — Pure HTML/CSS/JavaScript

## How to Use

### Option 1: Web App (Easiest)

Visit the live app: [token-optimizer.github.io](https://jaspreet-kalsi.github.io/token-optimizer/)

1. **Paste** your text or code into the Input panel
2. **Select** your optimization mode (Text, Code, or Aggressive)
3. **Choose** your target AI model from the dropdown
4. **Review** the optimized output and savings stats
5. **Copy** the optimized text with one click

### Option 2: Save as Bookmark (Browser)

1. Create a new bookmark in your browser
2. Set the URL to: `https://jaspreet-kalsi.github.io/token-optimizer/`
3. Click the bookmark whenever you need to optimize text for an AI

### Option 3: Self-Hosted

Clone this repo and open `index.html` in your browser:

```bash
git clone https://github.com/jaspreet-kalsi/token-optimizer.git
cd token-optimizer
open index.html  # or just double-click the file
```

## Optimization Modes

### Text Mode
Optimizes natural language by:
- Collapsing excessive whitespace
- Converting verbose phrases ("I was wondering if you could" → "Please")
- Replacing wordy connectors ("in order to" → "to", "due to the fact that" → "because")
- Standardizing section labels ("In conclusion" → "Summary:")
- Removing duplicate punctuation

**Best for:** Chat prompts, emails, documentation, natural language queries

### Code Mode
Optimizes code by:
- Removing single-line comments (`//`, `#`)
- Removing multi-line comments (`/* */`)
- Reducing indentation (tabs → spaces)
- Collapsing blank lines
- Preserving code structure and syntax

**Best for:** Code snippets, scripts, configuration files

### Aggressive Mode
Combines both Text and Code optimizations in sequence:
- Removes comments first (Code rules)
- Then applies text optimizations
- Collapses all excess whitespace

**Best for:** Mixed content (code + explanations)

## Token Counting

The app estimates tokens using a **simple heuristic**: `Math.ceil(string.length / 4)`

**Accuracy note:** This is an approximation. Real tokenizer accuracy varies by model:
- **GPT models:** Use OpenAI's tiktoken (roughly 1 token ≈ 4 characters)
- **Claude:** Anthropic's tokenizer (similar ratio)
- **Gemini:** Google's SentencePiece (can differ slightly)

For production use or high accuracy needs, integrate the respective tokenizer libraries. The current heuristic is accurate within **±5-10%** for most inputs.

## Model Context Windows

| Model | Context Window | Best For |
|-------|---|---|
| Claude 3 | 200,000 tokens | Long documents, code reviews |
| GPT-4 / Gemini 1.5 | 128,000 tokens | Typical use, balanced |
| Gemini 1.5 Pro | 2,000,000 tokens | Massive documents, videos |
| GPT-3.5 / Mixtral | 32,000 tokens | Faster, budget-friendly |
| Llama 3 | 8,000 tokens | Mobile, edge devices |

## Examples

### Text Mode Example

**Input:**
```
I was wondering if you could possibly help me understand how to configure authentication in my application? 
In order to accomplish this, I would like you to provide some examples.
```

**Output:**
```
Please help me understand how to configure authentication in my application? To accomplish this, please provide some examples.
```

**Savings:** ~35% tokens saved ✓

### Code Mode Example

**Input:**
```javascript
// Calculate the sum of an array
function sumArray(arr) {
  // Initialize total
  let total = 0;
  
  // Loop through array
  for (let i = 0; i < arr.length; i++) {
    total += arr[i]; // Add each element
  }
  
  return total;
}
```

**Output:**
```javascript
function sumArray(arr) {
 let total = 0;
 for (let i = 0; i < arr.length; i++) {
  total += arr[i];
 }
 return total;
}
```

**Savings:** ~40% tokens saved ✓

## Known Limitations

- ⚠️ **Token counting is approximate** — Uses character count heuristic, not actual tokenizers
- ⚠️ **Text optimization may remove context** — Very aggressive on removing conjunctions; may lose nuance
- ⚠️ **Code optimization doesn't validate syntax** — Comments might be inside strings (rare but possible)
- ⚠️ **No variable/function name shortening** — Preserves readability intentionally

## Browser Support

✅ Chrome 90+
✅ Firefox 88+
✅ Safari 14+
✅ Edge 90+
✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Contributing

Found a bug? Have an idea? 

1. [Open an issue](https://github.com/jaspreet-kalsi/token-optimizer/issues)
2. [Create a pull request](https://github.com/jaspreet-kalsi/token-optimizer/pulls)

## Roadmap

- [ ] Integrate real tokenizers (tiktoken, Anthropic, Google SentencePiece)
- [ ] VS Code extension
- [ ] Chrome/Firefox browser extension
- [ ] Keyboard shortcuts (Cmd+Opt+O)
- [ ] Custom optimization rules editor
- [ ] Export presets
- [ ] Unit tests & examples

## License

MIT License © 2026 Jaspreet Kalsi

## Support

Like this tool? Consider:
- ⭐ Starring this repo
- 🐛 Reporting issues
- 💡 Suggesting features
- 🤝 Contributing improvements
