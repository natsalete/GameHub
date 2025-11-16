<details>
<summary>🇧🇷 Versão em Português</summary>
  
# 🎮 GameHub - Explorador de Jogos

<p align="center">
  <img src="https://img.shields.io/badge/React%20Native-0.76-blue?style=for-the-badge&logo=react" />
  <img src="https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript" />
  <img src="https://img.shields.io/badge/Android-SDK%2033-green?style=for-the-badge&logo=android" />
  <img src="https://img.shields.io/badge/API-RAWG-red?style=for-the-badge" />
</p>

## 📱 Sobre o Projeto

**GameHub** é um aplicativo móvel desenvolvido em React Native que permite aos usuários explorar, buscar e gerenciar uma coleção de jogos. O app consome a API da RAWG (maior database de jogos do mundo) para fornecer informações detalhadas sobre milhares de jogos.

## 📸 Screenshots

<div style="display: flex; justify-content: center; gap: 10px;">
  <img src="https://github.com/user-attachments/assets/642ce897-1547-441f-be96-33d82220c86c" width="200" />
  <img src="https://github.com/user-attachments/assets/33fe38ef-8c99-4bf2-9388-926dee8d99c0" width="200" />
  <img src="https://github.com/user-attachments/assets/2fdb8024-b89b-4a15-ad68-9218387a4cb5" width="200" />
  <img src="https://github.com/user-attachments/assets/00f40696-bab7-46f4-91e0-c10ceccc0cde" width="200" />
</div>

### ✨ Funcionalidades Principais

- 🏠 **Home**: Lista de jogos populares com scroll infinito e pull-to-refresh
- 🔍 **Busca**: Pesquisa em tempo real com resultados instantâneos
- ❤️ **Favoritos**: Sistema de favoritos com persistência local
- 📊 **Detalhes**: Informações completas incluindo avaliações, screenshots, gêneros e plataformas
- 🎨 **UI Moderna**: Interface responsiva com design dark mode

---

## 🛠️ Tecnologias Utilizadas

### Core
- **React Native** - Framework mobile cross-platform
- **TypeScript** - Tipagem estática para JavaScript
- **React Hooks** - Gerenciamento de estado moderno

### Navegação
- **React Navigation** - Navegação entre telas
- **Stack Navigator** - Navegação hierárquica
- **Bottom Tabs** - Menu de navegação inferior

### Gerenciamento de Estado
- **React Context API** - Estado global da aplicação
- **AsyncStorage** - Persistência de dados local

### API & Networking
- **Axios** - Cliente HTTP para requisições
- **RAWG API** - Database de jogos

### UI/UX
- **React Native Screens** - Performance otimizada de navegação
- **Safe Area Context** - Suporte para notch e áreas seguras

---

## 📁 Estrutura do Projeto

```
GameHub/
├── src/
│   ├── components/          # Componentes reutilizáveis
│   │   ├── GameCard.tsx     # Card de jogo
│   │   └── SearchBar.tsx    # Barra de busca
│   ├── contexts/            # Contextos React
│   │   └── FavoritesContext.tsx  # Gerenciamento de favoritos
│   ├── navigation/          # Configuração de navegação
│   │   └── AppNavigator.tsx # Navegação principal
│   ├── screens/             # Telas do aplicativo
│   │   ├── HomeScreen.tsx   # Tela inicial
│   │   ├── SearchScreen.tsx # Tela de busca
│   │   ├── GameDetailsScreen.tsx  # Detalhes do jogo
│   │   └── FavoritesScreen.tsx    # Favoritos
│   ├── services/            # Serviços externos
│   │   └── api.ts           # Integração com RAWG API
│   └── types/               # Definições TypeScript
│       └── index.ts         # Tipos e interfaces
├── android/                 # Código nativo Android
├── ios/                     # Código nativo iOS
├── App.tsx                  # Componente raiz
└── package.json             # Dependências do projeto
```

---

## 🚀 Como Executar o Projeto

### Pré-requisitos

- Node.js (v18 ou superior)
- npm ou Yarn
- JDK 17
- Android Studio (para Android)
- Xcode (para iOS - apenas macOS)

### Instalação

1. **Clone o repositório**
```bash
git clone https://github.com/natsalete/GameHub.git
cd GameHub
```

2. **Instale as dependências**
```bash
npm install
# ou
yarn install
```

3. **Configure a API Key**

Obtenha uma chave gratuita em: https://rawg.io/apidocs

Edite o arquivo `src/services/api.ts`:
```typescript
const API_KEY = 'SUA_CHAVE_AQUI';
```

4. **Instale as dependências do iOS** (apenas macOS)
```bash
cd ios
pod install
cd ..
```

### Executar em Desenvolvimento

#### Android
```bash
# Terminal 1 - Iniciar Metro Bundler
npm start

# Terminal 2 - Executar no Android
npm run android
```

#### iOS (macOS apenas)
```bash
# Terminal 1 - Iniciar Metro Bundler
npm start

# Terminal 2 - Executar no iOS
npm run ios
```

---

## 📦 Gerar APK/AAB (Android)

### APK Debug (para testes)
```bash
cd android
./gradlew assembleDebug
cd ..
```
APK gerado em: `android/app/build/outputs/apk/debug/app-debug.apk`

### APK Release (produção)

1. **Gerar chave de assinatura** (apenas uma vez)
```bash
cd android/app
keytool -genkeypair -v -storetype PKCS12 -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
ou
& "C:\Program Files\Java\jdk-21\bin\keytool.exe" -genkeypair -v -storetype PKCS12 -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
cd ../..
```

2. **Configurar gradle.properties**

Adicione ao final de `android/gradle.properties`:
```properties
MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
MYAPP_RELEASE_KEY_ALIAS=my-key-alias
MYAPP_RELEASE_STORE_PASSWORD=sua_senha
MYAPP_RELEASE_KEY_PASSWORD=sua_senha
```

3. **Gerar APK**
```bash
cd android
./gradlew assembleRelease
cd ..
```
APK gerado em: `android/app/build/outputs/apk/release/app-release.apk`

### AAB para Google Play Store
```bash
cd android
./gradlew bundleRelease
cd ..
```
AAB gerado em: `android/app/build/outputs/bundle/release/app-release.aab`

---

## 🎨 Arquitetura e Padrões

### Gerenciamento de Estado
- **Context API** para estado global (favoritos)
- **useState** para estado local dos componentes
- **useEffect** para efeitos colaterais e chamadas à API

### Navegação
- **Stack Navigator** para navegação entre telas principais
- **Bottom Tabs** para navegação entre seções (Home, Busca, Favoritos)

### Comunicação com API
- Serviço centralizado em `api.ts`
- Requisições assíncronas com async/await
- Tratamento de erros com try/catch

### Tipagem TypeScript
- Interfaces para objetos de domínio (Game, Genre, Platform)
- Tipos para navegação (RootStackParamList, TabParamList)
- Props tipadas em todos os componentes

---

## 📊 Funcionalidades Detalhadas

### 1. Home Screen
- Lista de jogos mais populares
- Ordenação por rating
- Scroll infinito (paginação)
- Pull-to-refresh
- Navegação para detalhes

### 2. Search Screen
- Busca em tempo real
- Mínimo 3 caracteres
- Resultados instantâneos
- Grid responsivo
- Feedback visual de loading

### 3. Game Details Screen
- Banner do jogo
- Informações principais (rating, data de lançamento, Metacritic)
- Gêneros e plataformas
- Descrição completa
- Screenshots em carrossel horizontal
- Botão de favoritar/desfavoritar

### 4. Favorites Screen
- Lista de jogos favoritados
- Persistência com AsyncStorage
- Contador de favoritos
- Estado vazio amigável
- Remoção de favoritos

---

## 🎯 Requisitos Atendidos

### ✅ Interface de Usuário (UI)
- Design moderno e responsivo
- Componentes reutilizáveis (GameCard, SearchBar)
- Feedback visual (loading, estados vazios)
- Cores consistentes e harmoniosas

### ✅ Gerenciamento de Estado
- Context API para favoritos (estado global)
- AsyncStorage para persistência
- useState para estados locais

### ✅ Funcionalidades Interativas
- Busca em tempo real
- Listas dinâmicas com scroll infinito
- Sistema de favoritos
- Integração com API externa (RAWG)
- Pull-to-refresh

### ✅ Navegação
- React Navigation configurado
- Stack Navigator para fluxo principal
- Bottom Tabs para navegação entre seções
- Parâmetros tipados entre telas

---

## 🔧 Configurações e Customizações

### Cores do Tema
```typescript
const colors = {
  primary: '#1a1a2e',      // Azul escuro
  secondary: '#e94560',    // Rosa/vermelho
  accent: '#0f3460',       // Azul médio
  background: '#16213e',   // Azul card
  text: '#ffffff',         // Branco
  textSecondary: '#6c757d' // Cinza
};
```

### Alterar Nome do App
Edite `android/app/src/main/res/values/strings.xml`:
```xml
<string name="app_name">GameHub</string>
```

### Alterar Ícone
Substitua os arquivos em:
- `android/app/src/main/res/mipmap-*/ic_launcher.png`

---

## 🐛 Troubleshooting

### Metro Bundler não conecta
```bash
adb reverse tcp:8081 tcp:8081
```

### Erro de cache
```bash
npm start -- --reset-cache
```

### Limpar build Android
```bash
cd android
./gradlew clean
cd ..
```

### App não atualiza
```bash
adb uninstall com.gamehub
npm run android
```

---

## 📚 Recursos e Referências

- [React Native Documentation](https://reactnative.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [React Navigation](https://reactnavigation.org/)
- [RAWG API Documentation](https://rawg.io/apidocs)
- [AsyncStorage](https://react-native-async-storage.github.io/async-storage/)

---

## 👨‍💻 Autor

Desenvolvido com ☕ e 💙

- GitHub: [@natsalete](https://github.com/natsalete)
- LinkedIn: [Natália Salete](https://www.linkedin.com/in/natalia-salete-rodrigues/)
- Email: natsalete14@gmail.com

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests.

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

---

<div align="center">

### ⭐ Se gostou, deixe uma estrela! ⭐

**Feito com ❤️ e React Native**

</div>

</details>

# 🎮 GameHub - Game Explorer

<p align="center"> 
<img src="https://img.shields.io/badge/React%20Native-0.76-blue?style=for-the-badge&logo=react" /> 
<img src="https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript" /> 
<img src="https://img.shields.io/badge/Android-SDK%2033-green?style=for-the-badge&logo=android" /> 
<img src="https://img.shields.io/badge/API-RAWG-red?style=for-the-badge" />
</p>

## 📱 About the Project

**GameHub** is a mobile application developed in React Native app that allows users to explore, search, and manage a collection of games. The app consumes the RAWG API (the world's largest game database) to provide detailed information on thousands of games.

## 📸 Screenshots

<div style="display: flex; justify-content: center; gap: 10px;"> 
<img src="https://github.com/user-attachments/assets/642ce897-1547-441f-be96-33d82220c86c" width="200" /> 
<img src="https://github.com/user-attachments/assets/33fe38ef-8c99-4bf2-9388-926dee8d99c0" width="200" /> 
<img src="https://github.com/user-attachments/assets/2fdb8024-b89b-4a15-ad68-9218387a4cb5" width="200" /> 
<img src="https://github.com/user-attachments/assets/00f40696-bab7-46f4-91e0-c10ceccc0cde" width="200" />
</div>

### ✨ Main Features

- 🏠 **Home**: List of popular games with infinite scrolling and pull-to-refresh
- 🔍 **Search**: Real-time search with instant results
- ❤️ **Favorites**: Favorites system with local persistence
- 📊 **Details**: Complete information including ratings, screenshots, genres, and platforms
- 🎨 **Modern UI**: Responsive interface with dark mode design

---

## 🛠️ Technologies Used

### Core
- **React Native** - Cross-platform mobile framework
- **TypeScript** - Typing Static for JavaScript
- **React Hooks** - Modern state management

### Navigation
- **React Navigation** - Navigation between screens
- **Stack Navigator** - Hierarchical navigation
- **Bottom Tabs** - Bottom navigation menu

### State Management
- **React Context API** - Global application state
- **AsyncStorage** - Local data persistence

### API & Networking
- **Axios** - HTTP client for requests
- **RAWG API** - Game database

### UI/UX
- **React Native Screens** - Optimized navigation performance
- **Safe Area Context** - Support for notch and safe areas

---

## 📁 Project Structure

```
GameHub/
├── src/
│ ├── components/ # Components Reusable
│ │ ├── GameCard.tsx # Game card
│ │ └── SearchBar.tsx # Search bar
│ ├── contexts/ # React contexts
│ │ └── FavoritesContext.tsx # Favorites management
│ ├── navigation/ # Navigation configuration
│ │ └── AppNavigator.tsx # Main navigation
│ ├── screens/ # App screens
│ │ ├── HomeScreen.tsx # Home screen
│ │ ├── SearchScreen.tsx # Search screen
│ │ ├── GameDetailsScreen.tsx # Game details
│ │ └── FavoritesScreen.tsx # Favorites
│ ├── services/ # External services
│ │ └── api.ts # RAWG API integration
│ └── types/ # TypeScript definitions
│ └── index.ts # Types and interfaces
├── android/ # Native Android code
├── ios/ # Native iOS code
├── App.tsx # Root component
└── package.json # Project dependencies

```

---

## 🚀 How to Run The Project

### Prerequisites

- Node.js (v18 or higher)
- npm or Yarn
- JDK 17
- Android Studio (for Android)
- Xcode (for iOS - macOS only)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/natsalete/GameHub.git
cd GameHub
```

2. **Install the dependencies**
```bash
npm install

# or
yarn install
```

3. **Configure the API Key**

Get a free key at: https://rawg.io/apidocs

Edit the `src/services/api.ts` file:

```typescript
const API_KEY = 'YOUR_KEY_HERE'; ```

4. **Install iOS dependencies** (macOS only)
```bash
cd ios
pod install
cd ..
```

### Run in Development

#### Android
```bash
# Terminal 1 - Start Metro Bundler
npm start

# Terminal 2 - Run on Android
npm run android
```

#### iOS (macOS only)
```bash
# Terminal 1 - Start Metro Bundler
npm start

# Terminal 2 - Run on iOS
npm run ios
```
---

## 📦 Generate APK/AAB (Android)

### APK Debug (for testing)
```bash
cd android
./gradlew assembleDebug
cd ..
```
APK generated in: `android/app/build/outputs/apk/debug/app-debug.apk`

### APK Release (production)

1. **Generate signing key** (only once)
```bash
cd android/app
keytool -genkeypair -v -storetype PKCS12 -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
or
& "C:\Program Files\Java\jdk-21\bin\keytool.exe" -genkeypair -v -storetype PKCS12 -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
cd ../..
```

2. **Configure gradle.properties**

Add the following to the end of `android/gradle.properties`:
```properties
MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
MYAPP_RELEASE_KEY_ALIAS=my-key-alias
MYAPP_RELEASE_STORE_PASSWORD=your_password
MYAPP_RELEASE_KEY_PASSWORD=your_password
```

3. **Generate APK**
```bash
cd android
./gradlew assembleRelease
cd ..
```
APK generated in: `android/app/build/outputs/apk/release/app-release.apk`

### AAB for Google Play Store
```bash
cd android
./gradlew bundleRelease
cd ..
``` AAB generated in: `android/app/build/outputs/bundle/release/app-release.aab`

---

## 🎨 Architecture and Patterns

### State Management
- **Context API** for global state (favorites)
- **useState** for local component state
- **useEffect** for side effects and API calls

### Navigation
- **Stack Navigator** for navigation between main screens
- **Bottom Tabs** for navigation between sections (Home, Search, Favorites)

### API Communication
- Centralized service in `api.ts`
- Asynchronous requests with async/await
- Error handling with try/catch

### TypeScript Typing
- Interfaces for domain objects (Game, Genre, Platform)
- Types for navigation (RootStackParamList, TabParamList)
- Typed props in all components

---

## 📊 Detailed Features

### 1. Home Screen
- List of most popular games
- Sorting by rating
- Infinite scrolling (pagination)
- Pull-to-refresh
- Navigation to details

### 2. Search Screen
- Real-time search
- Minimum 3 characters
- Instant results
- Responsive grid
- Visual loading feedback

### 3. Game Details Screen
- Game banner
- Main information (rating, release date, Metacritic)
- Genres and platforms
- Full description
- Screenshots in horizontal carousel
- Favorite/unfavorite button

### 4. Favorites Screen
- List of games Favorites
- Persistence with AsyncStorage
- Favorites counter
- Friendly empty state
- Favorites removal

---

## 🎯 Requirements Met

### ✅ User Interface (UI)
- Modern and responsive design
- Reusable components (GameCard, SearchBar)
- Visual feedback (loading, empty states)
- Consistent and harmonious colors

### ✅ State Management
- Context API for favorites (global state)
- AsyncStorage for persistence
- useState for local states

### ✅ Interactive Features
- Real-time search
- Dynamic lists with infinite scroll
- Favorites system
- Integration with external API (RAWG)
- Pull-to-refresh

### ✅ Navigation
- React Navigation configured
- Stack Navigator for main flow
- Bottom Tabs for navigation between sections
- Typed parameters between Screens

---

## 🔧 Settings and Customizations

### Theme Colors
```typescript
const colors = {
primary: '#1a1a2e', // Dark blue
secondary: '#e94560', // Pink/red
accent: '#0f3460', // Medium blue
background: '#16213e', // Card blue
text: '#ffffff', // White

textSecondary: '#6c757d' // Gray
};
```

### Change App Name
Edit `android/app/src/main/res/values/strings.xml`:

```xml
<string name="app_name">GameHub</string>
```

### Change Icon
Replace the files in:
- `android/app/src/main/res/mipmap-*/ic_launcher.png`

---

## 🐛 Troubleshooting

### Metro Bundler not connecting
```bash
adb reverse tcp:8081 tcp:8081

```

### Cache error
```bash
npm start -- --reset-cache
```

### Clear Android build
```bash
cd android
./gradlew clean
cd ..
```

### App not updating
```bash
adb uninstall com.gamehub
npm run android
```

---

## 📚 Resources and References

- [React Native Documentation](https://reactnative.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [React Navigation](https://reactnavigation.org/)
- [RAWG API Documentation](https://rawg.io/apidocs)
- [AsyncStorage](https://react-native-async-storage.github.io/async-storage/)

---

## 👨‍💻 Author

Powered by ☕ and 💙

- GitHub: [@natsalete](https://github.com/natsalete)
- LinkedIn: [Natália Salete](https://www.linkedin.com/in/natalia-salete-rodrigues/)

- Email: natsalete14@gmail.com

---

## 📄 License

This project is under the MIT license. See the [LICENSE](LICENSE) file for more details.

---

## 🤝 Contributions

Contributions are welcome! Feel free to open issues and pull requests.

1. Fork the project
2. Create a branch for your feature (`git checkout -b Add feature/MyFeature`)
3. Commit your changes (`git commit -m 'Add MyFeature'`)
4. Push to the branch (`git push origin feature/MyFeature`)
5. Open a Pull Request

---

<div align="center">

### ⭐ If you liked it, leave a star! ⭐

**Made with ❤️ and React Native**

</div>
