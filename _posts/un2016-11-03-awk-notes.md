---
layout:     post
title:      awk学习笔记
category: blog
description: ..
---


awk求某一列的和

	awk 'BEGIN{sum=0}{sum+=$1}END{print sum}' data.txt

