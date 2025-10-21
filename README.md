<h1 align="center">👋 Salom, men Xolmuhammadman</h1>

---

## 🌐 Mening ijtimoiy tarmoqlarim
<p align="center">
  <a href="https://www.instagram.com/azerbaydjan_009?igsh=MXhhajF0MDJ1c2VjNA==" target="_blank">
    <img src="https://img.shields.io/badge/Instagram-azerbaydjan__009-orange?style=for-the-badge&logo=instagram" />
  </a>
  <a href="https://www.instagram.com/handsome_n_1?igsh=ZmhidWNyYnA2ajY1" target="_blank">
    <img src="https://img.shields.io/badge/Instagram-handsome__n__1-pink?style=for-the-badge&logo=instagram" />
  </a>
</p>

---

## 📊 Statistikam
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=YourUsername&show_icons=true&theme=radical" alt="GitHub Stats" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=YourUsername&layout=compact&theme=radical" alt="Top Languages" />
</p>

---

<p align="center">✨ Mening profilimga tashrif buyurganingiz uchun rahmat ✨</p>

<p align="center">
  <img src="https://media1.giphy.com/media/gM5qFksULw54NMWyry/giphy.gif?cid=ecf05e47zgvaqz03cae4ugawpvo0ghsc4v2cq4u4zwd40ta&rid=giphy.gif&ct=s" width="300"/>
</p>
#___________________________
#!/usr/bin/env node

import React, { useState, useEffect } from 'react';
import { render, Box, Text, useApp } from 'ink';

// Terminal UI komponenti
const App = () => {
	const { exit } = useApp();
	const [dots, setDots] = useState('');
	const [progress, setProgress] = useState(0);
	const [message, setMessage] = useState('Iltimos kuting');

	useEffect(() => {
		const interval = setInterval(() => {
			setDots(prev => (prev.length < 3 ? prev + '.' : ''));

			setProgress(prev => {
				if (prev >= 100) {
					clearInterval(interval);
					setMessage('Tayyor!');
					setTimeout(() => exit(), 1500);
					return 100;
				}
				return prev + 5;
			});
		}, 200);

		return () => clearInterval(interval);
	}, []);

	return (
		<Box
			borderStyle="round"
			borderColor="cyan"
			padding={1}
			flexDirection="column"
			alignItems="center"
			width={40}
		>
			<Text color="green">{message}{dots}</Text>
			<Text>Progress: {progress}%</Text>
		</Box>
	);
};

// Render qilish
render(<App />);


