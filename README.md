# MIT504

The files containing the topics for your PowerPoint presentation have already been uploaded here. To streamline the process, utilize the recording features of MS PowerPoint to record each page and export them to video format.


Sample Video Upload

https://github.com/user-attachments/assets/1f9e5b61-8426-4fcc-899e-af502dac93b0

# Definition of Linear Regression

Linear regression is a statistical method that models the relationship between a dependent variable \( y \) and one or more independent variables \( x_1, x_2, \ldots, x_p \). It assumes a linear relationship, which can be represented by a straight line when plotted.

## Historical Background and Development

Developed in the early 19th century, linear regression has evolved through advancements in statistical theory and computing power, becoming a cornerstone of predictive modeling in data science and machine learning.

## Importance in Data Science and Machine Learning

Linear regression is fundamental for understanding relationships between variables, making predictions, and interpreting data trends. It serves as a basis for more complex machine learning algorithms and statistical models.

## Basic Concepts

- **Linear relationship between variables:** Assumes a linear correlation between predictors and the response variable.
- **Assumptions of linear regression:** Includes linearity, independence of errors, homoscedasticity, and normality of residuals.
- **Simple vs. multiple linear regression:** Simple uses one predictor, while multiple incorporates multiple predictors.

## Mathematical Formulation

- **Regression equation:** \( y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_p x_p + \epsilon \)
- **Interpretation of coefficients (\( \beta \))**: Each \( \beta \) quantifies the effect of its corresponding \( x \)-variable on \( y \).
- **Ordinary Least Squares (OLS) method**: Minimizes the sum of squared differences between observed and predicted values to estimate \( \beta \).

## Model Evaluation

- **Assessing model fit:** \( R^2 \), adjusted \( R^2 \) measure how well the model fits the data.
- **Residual analysis:** Examines the difference between predicted and actual values for model validity.
- **Assumptions validation:** Ensures residuals meet statistical assumptions.

## Types of Linear Regression

- **Simple Linear Regression:** Predicts \( y \) using one predictor.
- **Multiple Linear Regression:** Uses multiple predictors to predict \( y \).
- **Polynomial Regression:** Models non-linear relationships using polynomial terms.

## Applications of Linear Regression

- **Technology Project Management:** Predicts project timelines based on historical data.
- **Quality Assurance:** Analyzes factors affecting product quality.
- **Marketing Analysis:** Forecasts sales based on advertising spend.
- **Financial Forecasting:** Predicts stock prices or market trends.

## Implementation Process

- **Data Collection:** Gathers relevant data for analysis.
- **Data Preprocessing:** Cleans and prepares data for regression.
- **Applying Linear Regression:** Implements using tools like Python or R.
- **Interpreting Results:** Analyzes model output to make data-driven decisions.

## Tools and Technologies

- Overview of tools like scikit-learn in Python and lm() function in R.
- Example code snippets and demonstrations.

## Challenges and Considerations

- **Overfitting vs. underfitting:** Balancing model complexity.
- **Multicollinearity:** Addressing correlation among predictors.
- **Handling outliers and missing data:** Techniques for robust modeling.

## Real-World Examples

- Case studies demonstrating successful applications in various industries.

## Comparison with Other Techniques

- **Other regression algorithms:** Ridge Regression, Lasso Regression.
- **Strengths and weaknesses:** Comparison with linear regression.

## Google Colab

[Up{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": []
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "source": [
        "**Simple Linear Regression**"
      ],
      "metadata": {
        "id": "KP8g-VKM-5JW"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **1. Import Libraries**"
      ],
      "metadata": {
        "id": "IA06yhkv0ms2"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "V7TVvwcgz2gy"
      },
      "outputs": [],
      "source": [
        "import pandas as pd #Data Manipulation\n",
        "import numpy as np #Numerical Operation\n",
        "import matplotlib.pyplot as plt #Data Visualization\n",
        "from sklearn.linear_model import LinearRegression #Data Modeling"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **2. Generating Random Data:**"
      ],
      "metadata": {
        "id": "fUuAQ1aE2Af-"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "X = [3, 1, 2, 6, 4]\n",
        "Y = [90, 85, 88, 98, 91]\n"
      ],
      "metadata": {
        "id": "6zbIdMoQ2Hl8"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **3. Creating DataFrame and Saving to CSV**"
      ],
      "metadata": {
        "id": "e0xmf70t4OWP"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "data = pd.DataFrame({'X': X,'Y': Y})\n",
        "\n",
        "data.to_csv('data.csv',index=False)\n",
        "\n",
        "print(data.head())"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "bz80NtUC4P-e",
        "outputId": "d7a93c26-c2ee-4b72-edcb-ebf3aa07f8a7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "   X   Y\n",
            "0  3  90\n",
            "1  1  85\n",
            "2  2  88\n",
            "3  6  98\n",
            "4  4  91\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **4. Visualizing the Data**"
      ],
      "metadata": {
        "id": "8p8a9zVh6xzg"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "plt.scatter(data['X'],data['Y'])\n",
        "plt.xlabel('Independent Variable (X)')\n",
        "plt.ylabel('Dependent Variable (Y)')\n",
        "plt.title('Scatter Plot of Data')\n",
        "plt.show()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 472
        },
        "id": "nV5RxQTR6yKp",
        "outputId": "c803d006-995f-4b3b-9d3b-29521190d51a"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAjMAAAHHCAYAAABKudlQAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMSwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/bCgiHAAAACXBIWXMAAA9hAAAPYQGoP6dpAABKlElEQVR4nO3deVxV1f7/8fcBZRDhKCoKiohaAk45kGkODY5fQ0srMytFrdvNMrOovOWAQw7dBu126VfeRLHSBi3NEi2nTE3LnM15FvPmwKSiwvr94cNzPQF6joLHTa/n43Eej9h77bU/52Cet2uvvbbNGGMEAABgUV6eLgAAAOBaEGYAAIClEWYAAIClEWYAAIClEWYAAIClEWYAAIClEWYAAIClEWYAAIClEWYAAIClEWYAWMbevXtls9mUnJzs6VKczJ8/X7fccov8/Pxks9l08uRJT5cE/KUQZoAbwMaNG3X//fcrIiJCfn5+qlq1qtq1a6d33nmn2M758ccf6+233863/fDhwxoxYoTWrVtXbOf+syVLlshmszlepUuXVs2aNfXYY49p9+7dRXKOFStWaMSIEUUeNI4dO6YHH3xQ/v7+evfdd5WSkqKAgIAC2yYnJzu9Tz8/P4WFhalDhw6aNGmSMjMzr7qO4np/gBUQZgAPW7FihZo2bar169fr8ccf17/+9S/1799fXl5emjhxYrGd93JhJjEx8bqGmYsGDhyolJQUvf/+++rcubNmzpyp2NhYHT58+Jr7XrFihRITE4v8y37NmjXKzMzUqFGj1K9fPz3yyCMqXbr0ZY8ZOXKkUlJSlJSUpGeeeUaSNGjQINWvX18bNmy4qjqK6/0BVlDK0wUAf3VjxoyR3W7XmjVrVK5cOad9R48e9UxRxSA7O7vQEYuLWrVqpfvvv1+SFB8fr5tvvlkDBw7U1KlTNWTIkOtRptsu/o7+/Lu7nE6dOqlp06aOn4cMGaJFixbpnnvuUZcuXbR161b5+/sXdalAicXIDOBhu3btUt26dQv8MgwJCcm3bfr06br11ltVpkwZlS9fXq1bt9aCBQsc+7/66it17txZYWFh8vX1Va1atTRq1Cjl5uY62txxxx2aN2+e9u3b57jkUaNGDS1ZskSxsbGSLoSJi/sunaPy008/qWPHjrLb7SpTpozatGmjH3/80anGESNGyGazacuWLXr44YdVvnx5tWzZ0u3P5q677pIk7dmz57LtFi1apFatWikgIEDlypVT165dtXXrVqd6EhISJEmRkZGO97V3797L9vvZZ5+pSZMm8vf3V8WKFfXII4/o0KFDjv133HGHevfuLUmKjY2VzWZTnz593H6f0oX3OnToUO3bt0/Tp093bN+wYYP69OmjmjVrys/PT1WqVFHfvn117Ngxl9/flClTdNdddykkJES+vr6KiYlRUlLSVdUJ3IgYmQE8LCIiQitXrtSmTZtUr169y7ZNTEzUiBEj1KJFC40cOVI+Pj766aeftGjRIrVv317ShXkZZcuW1eDBg1W2bFktWrRIw4YNU0ZGhl5//XVJ0iuvvKL09HQdPHhQb731liSpbNmyio6O1siRIzVs2DA98cQTatWqlSSpRYsWki6Ehk6dOqlJkyYaPny4vLy8HF+UP/zwg2699Vaneh944AHddNNNeu2112SMcfuz2bVrlySpQoUKhbb57rvv1KlTJ9WsWVMjRozQ6dOn9c477+j222/X2rVrVaNGDXXr1k3bt2/XJ598orfeeksVK1aUJFWqVKnQfpOTkxUfH6/Y2FiNHTtWv//+uyZOnKgff/xRv/76q8qVK6dXXnlFderU0fvvv6+RI0cqMjJStWrVcvt9XvToo4/qH//4hxYsWKDHH39ckrRw4ULt3r1b8fHxqlKlijZv3qz3339fmzdv1qpVq2Sz2a74/pKSklS3bl116dJFpUqV0ty5c/XUU08pLy9PAwYMuOp6gRuGAeBRCxYsMN7e3sbb29s0b97cvPjiiyY1NdWcPXvWqd2OHTuMl5eXue+++0xubq7Tvry8PMd/nzp1Kt85/va3v5kyZcqYM2fOOLZ17tzZRERE5Gu7Zs0aI8lMmTIl3zluuukm06FDh3zni4yMNO3atXNsGz58uJFkevbs6dJnsHjxYiPJfPjhh+a///2vOXz4sJk3b56pUaOGsdlsZs2aNcYYY/bs2ZOvtltuucWEhISYY8eOObatX7/eeHl5mccee8yx7fXXXzeSzJ49e65Yz9mzZ01ISIipV6+eOX36tGP7119/bSSZYcOGObZNmTLFSHLUeDmutLXb7aZRo0aOnwv6fX7yySdGklm2bJlj2+XeX0F9dOjQwdSsWfOKNQNWwGUmwMPatWunlStXqkuXLlq/fr0mTJigDh06qGrVqpozZ46j3Zdffqm8vDwNGzZMXl7O/+vabDbHf1861yIzM1N//PGHWrVqpVOnTum333676jrXrVunHTt26OGHH9axY8f0xx9/6I8//lB2drbuvvtuLVu2THl5eU7HPPnkk26do2/fvqpUqZLCwsLUuXNnZWdna+rUqU7zSy6VlpamdevWqU+fPgoODnZsb9Cggdq1a6dvvvnG/Tcq6eeff9bRo0f11FNPyc/Pz7G9c+fOioqK0rx5866qX1eULVvW6a6mS3+fZ86c0R9//KHbbrtNkrR27VqX+ry0j/T0dP3xxx9q06aNdu/erfT09CKqHPAcLjMBN4DY2FjNmjVLZ8+e1fr16zV79my99dZbuv/++7Vu3TrFxMRo165d8vLyUkxMzGX72rx5s1599VUtWrRIGRkZTvuu5Ytrx44dkuSYI1KQ9PR0lS9f3vFzZGSkW+cYNmyYWrVqJW9vb1WsWFHR0dEqVarwv6b27dsnSapTp06+fdHR0UpNTXVp4rE7/UZFRWn58uVu9eeOrKwsp7lSx48fV2JiombMmJFvQrirv88ff/xRw4cP18qVK3Xq1Kl8fdjt9msvHPAgwgxwA/Hx8VFsbKxiY2N18803Kz4+Xp999pmGDx/u0vEnT55UmzZtFBQUpJEjR6pWrVry8/PT2rVr9dJLL+UbOXHHxWNff/113XLLLQW2KVu2rNPP7t6RU79+fbVt2/aq6isJDh48qPT0dNWuXdux7cEHH9SKFSuUkJCgW265RWXLllVeXp46duzo0u9z165duvvuuxUVFaU333xT4eHh8vHx0TfffKO33nrrmv5MADcKwgxwg7p4aSUtLU2SVKtWLeXl5WnLli2FhoklS5bo2LFjmjVrllq3bu3YXtDdQJdemnJl+8WJrUFBQTdM4IiIiJAkbdu2Ld++3377TRUrVnSMyhT2vq7U78U7qi7atm2bY39RS0lJkSR16NBBknTixAl9//33SkxM1LBhwxztLo6SXaqw9zd37lzl5ORozpw5ql69umP74sWLi7J0wKOYMwN42OLFiwu80+fifI+LlzruvfdeeXl5aeTIkfn+NX3xeG9vb6efJens2bP697//na//gICAAi9TXPzy//Pia02aNFGtWrX0z3/+U1lZWfmO++9//1voeywuoaGhuuWWWzR16lSnejdt2qQFCxbo//7v/xzbCntfBWnatKlC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0pKk++67T++9954mTJig+vXra/Lkyfriiy/UsmVLT5YNAABuIB5bZ+Z6YZ0ZAACsxxLrzAAAABQFwgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALA0wgwAALC0Uldz0P79+7Vv3z6dOnVKlSpVUt26deXr61vUtQEAAFyRy2Fm7969SkpK0owZM3Tw4EEZYxz7fHx81KpVKz3xxBPq3r27vLwY8AEAANeHS6lj4MCBatiwofbs2aPRo0dry5YtSk9P19mzZ3XkyBF98803atmypYYNG6YGDRpozZo1xV03AACAJBdHZgICArR7925VqFAh376QkBDddddduuuuuzR8+HDNnz9fBw4cUGxsbJEXCwAA8Gc2c+n1osswxshmsxV3PUUuIyNDdrtd6enpCgoK8nQ5AADABe58f7s8ueX222/Xzp07r7k4AACAouRymKlWrZpuueUWvfvuu8VZDwAAgFtcDjOffvqppkyZopEjR6pdu3Y6ePBgcdYFAADgErfWmXnggQd0xx13aMCAAapfv74effRRlSrl3MWbb75ZpAUCAABcjtuL5gUHBys6OlqzZ8/Wr7/+6hRmrDhBGAAAWJtbq9tt3rxZt956q6ZNm6YFCxbohx9+0OLFix2vRYsWuV1AZmamBg0apIiICPn7+6tFixaFrlPz5JNPymaz6e2333b7PAAAoGRyOcyMGzdOTZo0UcOGDbVhwwbdeeedRVJA//79tXDhQqWkpGjjxo1q37692rZtq0OHDjm1mz17tlatWqWwsLAiOS8AACgZXA4zEydO1GeffaYPP/xQgYGBRXLy06dP64svvtCECRPUunVr1a5dWyNGjFDt2rWVlJTkaHfo0CE988wz+uijj1S6dOkiOTcAACgZXJ4zs2nTpgJXAL4W58+fV25urvz8/Jy2+/v7a/ny5ZKkvLw8Pfroo0pISFDdunWv2GdOTo5ycnIcP2dkZBRpzQAA4Mbi0sjMjBkzXA4yBw4c0I8//uhS28DAQDVv3lyjRo3S4cOHlZubq+nTp2vlypVKS0uTJI0fP16lSpXSwIEDXepz7Nixstvtjld4eLhLxwEAAGtyKcwkJSUpOjpaEyZM0NatW/PtT09P1zfffKOHH35YjRs31rFjx1wuICUlRcYYVa1aVb6+vpo0aZJ69uwpLy8v/fLLL5o4caKSk5NdvlNqyJAhSk9Pd7wOHDjgci0AAMB6XH4205w5c/TOO+9o0aJFCggIUOXKleXn56cTJ07oyJEjqlixovr06aPnnntOlStXdruQ7OxsZWRkKDQ0VD169FBWVpbatWunwYMHy8vrf5krNzdXXl5eCg8P1969e6/YL89mAgDAetz5/nY5zFz0xx9/aPny5dq3b59Onz6tihUrqlGjRmrUqJFT6LhaJ06cUGRkpCZMmKDu3bs7Ljdd1KFDBz366KOKj49XnTp1rtgfYQYAAOtx5/vb7UXzKlasqHvvvfdqa8snNTVVxhjVqVNHO3fuVEJCgqKiohQfH6/SpUvnm6tTunRpValSxaUgAwAASr5rH0q5Runp6RowYICioqL02GOPqWXLlkpNTeUWbAAA4BK3LzNZDZeZAACwHne+vz0+MgMAAHAtCDMAAMDSrjrMnD17Vtu2bdP58+eLsh4AAAC3uB1mTp06pX79+qlMmTKqW7eu9u/fL0l65plnNG7cuCIvEAAA4HLcDjNDhgzR+vXrtWTJEqdnKrVt21YzZ84s0uIAAACuxO11Zr788kvNnDlTt912m9MjBurWratdu3YVaXEAAABX4vbIzH//+1+FhITk256dne3y85MAAACKitthpmnTppo3b57j54sBZvLkyWrevHnRVQYAAOACty8zvfbaa+rUqZO2bNmi8+fPa+LEidqyZYtWrFihpUuXFkeNAAAAhXJ7ZKZly5Zat26dzp8/r/r162vBggUKCQnRypUr1aRJk+KoEQAAoFA8zgAAANxwivyp2RkZGS6fnMAAAACuJ5fCTLly5a54p5IxRjabTbm5uUVSGAAAgCtcCjOLFy8u7joAAACuikthpk2bNsVdBwAAwFVx+9ZsSTpx4oT+85//aOvWrZKkmJgYxcfHKzg4uEiLAwAAuBK3b81etmyZatSooUmTJunEiRM6ceKEJk2apMjISC1btqw4agQAACiU27dm169fX82bN1dSUpK8vb0lSbm5uXrqqae0YsUKbdy4sVgKvVrcmg0AgPW48/3t9sjMzp079fzzzzuCjCR5e3tr8ODB2rlzp/vVAgAAXAO3w0zjxo0dc2UutXXrVjVs2LBIigIAAHCVSxOAN2zY4PjvgQMH6tlnn9XOnTt12223SZJWrVqld999V+PGjSueKgEAAArh0pwZLy8v2Ww2XanpjbhoHnNmAACwniJ/nMGePXuKpDAAAICi5lKYiYiIKO46AAAArspVLZonSVu2bNH+/ft19uxZp+1dunS55qIAAABc5XaY2b17t+677z5t3LjRaR7NxQdR3mhzZgAAQMnm9q3Zzz77rCIjI3X06FGVKVNGmzdv1rJly9S0aVMtWbKkGEoEAAAonNsjMytXrtSiRYtUsWJFeXl5ycvLSy1bttTYsWM1cOBA/frrr8VRJwAAQIHcHpnJzc1VYGCgJKlixYo6fPiwpAuThLdt21a01QEAAFyB2yMz9erV0/r16xUZGalmzZppwoQJ8vHx0fvvv6+aNWsWR40AAACFcjvMvPrqq8rOzpYkjRw5Uvfcc49atWqlChUqaObMmUVeIAAAwOW4/dTsghw/flzly5d33NF0I2EFYAAArKfIVwC+kuDg4KLoBgAAwG0uhZlu3bopOTlZQUFB6tat22Xbzpo1q0gKAwAAcIVLYcZutzsuIdnt9mItCAAAwB1uzZkxxujAgQOqVKmS/P39i7OuIsOcGQAArMed72+31pkxxqh27do6ePDgNRUIAABQVNwKM15eXrrpppt07Nix4qoHAADALW6vADxu3DglJCRo06ZNxVEPAACAW9xeZ6Z8+fI6deqUzp8/Lx8fn3xzZ44fP16kBV4r5swAAGA9xbrOzNtvv321dQEAABQ5t8NM7969i7SAzMxMDR06VLNnz9bRo0fVqFEjTZw4UbGxsTp37pxeffVVffPNN9q9e7fsdrvatm2rcePGKSwsrEjrAAAA1uT2nJlLnTlzRhkZGU4vd/Xv318LFy5USkqKNm7cqPbt26tt27Y6dOiQTp06pbVr12ro0KFau3atZs2apW3btqlLly7XUjYAAChB3J4zk52drZdeekmffvppgXc15ebmutzX6dOnFRgYqK+++kqdO3d2bG/SpIk6deqk0aNH5ztmzZo1uvXWW7Vv3z5Vr179iudgzgwAANZTbOvMSNKLL76oRYsWKSkpSb6+vpo8ebISExMVFhamadOmudXX+fPnlZubKz8/P6ft/v7+Wr58eYHHpKeny2azqVy5cgXuz8nJuebRIgAAYB1uh5m5c+fq3//+t7p3765SpUqpVatWevXVV/Xaa6/po48+cquvwMBANW/eXKNGjdLhw4eVm5ur6dOna+XKlUpLS8vX/syZM3rppZfUs2fPQlPa2LFjZbfbHa/w8HB33yIAALAQt8PM8ePHVbNmTUlSUFCQ41bsli1batmyZW4XkJKSImOMqlatKl9fX02aNEk9e/aUl5dzaefOndODDz4oY4ySkpIK7W/IkCFKT093vA4cOOB2TQAAwDrcDjM1a9bUnj17JElRUVH69NNPJV0YsSns0s/l1KpVS0uXLlVWVpYOHDig1atX69y5c47AJP0vyOzbt08LFy687LUzX19fBQUFOb0AAEDJ5XaYiY+P1/r16yVJL7/8st599135+fnpueeeU0JCwlUXEhAQoNDQUJ04cUKpqanq2rWrpP8FmR07dui7775ThQoVrvocAACg5HH5bqYXXnhB/fv3V1RUlNP2ffv26ZdfflHt2rXVoEEDtwtITU2VMUZ16tTRzp07lZCQID8/P/3www+SpPvvv19r167V119/rcqVKzuOCw4Olo+PzxX7524mAACsx53vb5fDzE033aTdu3erWbNm6t+/v3r06KGAgIBrLvbTTz/VkCFDdPDgQQUHB6t79+4aM2aM7Ha79u7dq8jIyAKPW7x4se64444r9k+YAQDAeoolzEjSsmXL9OGHH+qLL76QJD3wwAPq37+/WrRocW0VFyPCDAAA1lNs68y0bt1aycnJOnLkiCZOnKgdO3aoZcuWio6O1j//+U/9/vvv11Q4AACAu9xeAfjPdu7cqSlTpui9995TVlaWcnJyiqq2IsHIDAAA1lOsKwBfKjs7Wz/88IOWLl2qEydOON1ODQAAcD1cVZhZvny5+vbtq9DQUA0cOFA333yzfvjhB23durWo6wMAALisUq42TEtL09SpU5WcnKzt27frtttu05tvvqmHHnpIZcuWLc4aAQAACuVymAkPD1eFChX06KOPql+/foqOji7OugAAAFzicpj59NNP1aVLF5Uq5fIhAAAAxc7lZNKtW7firAMAAOCqXNPdTAAAAJ5GmAEAAJZGmAEAAJbmdpjp27evMjMz823Pzs5W3759i6QoAAAAV7kd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cnNzNWbMGPXq1cvR5p133tETTzyhatWqqVSpUvLy8tIHH3yg1q1bF9jn2LFjlZiYeL3eAorB0czCg8zVtAMAlGweHZn59NNP9dFHH+njjz/W2rVrNXXqVP3zn//U1KlTHW3eeecdrVq1SnPmzNEvv/yiN954QwMGDNB3331XYJ9DhgxRenq643XgwIHr9XZQREIC/Yq0HQCgZLOZS28dus7Cw8P18ssva8CAAY5to0eP1vTp0/Xbb7/p9OnTstvtmj17tjp37uxo079/fx08eFDz58+/4jkyMjJkt9uVnp6uoKCgYnkfKFq5eUYtxy/SkfQzBc6bsUmqYvfT8pfu4jZtACih3Pn+9ujIzKlTp+Tl5VyCt7e38vLyJEnnzp3TuXPnLtsGJY+3l03D42IkXQgul7r48/C4GIIMAECSh+fMxMXFacyYMapevbrq1q2rX3/9VW+++ab69u0rSQoKClKbNm2UkJAgf39/RUREaOnSpZo2bZrefPNNT5aOYtaxXqiSHmmsxLlbnCYDV7H7aXhcDLdlAwAcPHqZKTMzU0OHDtXs2bN19OhRhYWFqWfPnho2bJh8fHwkSUeOHNGQIUO0YMECHT9+XBEREXriiSf03HPPyWa78r/MucxkbawADAB/Te58f3s0zFwPhBkAAKzHMnNmAAAArhVhBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWBphBgAAWJpHw0xubq6GDh2qyMhI+fv7q1atWho1apSMMU7ttm7dqi5dushutysgIECxsbHav3+/h6oGAAA3klKePPn48eOVlJSkqVOnqm7duvr5558VHx8vu92ugQMHSpJ27dqlli1bql+/fkpMTFRQUJA2b94sPz8/T5YOAABuEDbz52GQ6+iee+5R5cqV9Z///MexrXv37vL399f06dMl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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **5. Preparing Data for Modeling**"
      ],
      "metadata": {
        "id": "VhPyrI8U9kzU"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "X = data[['X']] #Independent Variable\n",
        "Y = data[['Y']] #Dependent Variable"
      ],
      "metadata": {
        "id": "RbiJDKDK9msg"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **6. Fitting the Linear Regression Model**"
      ],
      "metadata": {
        "id": "ZHP3Tkuh-eYO"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "model  = LinearRegression()\n",
        "\n",
        "model.fit(X,Y)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 75
        },
        "id": "UphrQsaY-fX_",
        "outputId": "44d2affe-883f-4e9b-91c6-c322bc7152b8"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "LinearRegression()"
            ],
            "text/html": [
              "<style>#sk-container-id-2 {color: black;background-color: white;}#sk-container-id-2 pre{padding: 0;}#sk-container-id-2 div.sk-toggleable {background-color: white;}#sk-container-id-2 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-2 label.sk-toggleable__label-arrow:before {content: \"▸\";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-2 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-2 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-2 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-2 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-2 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-2 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: \"▾\";}#sk-container-id-2 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-2 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-2 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-2 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-2 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-2 div.sk-parallel-item::after {content: \"\";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-2 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-2 div.sk-serial::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-2 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-2 div.sk-item {position: relative;z-index: 1;}#sk-container-id-2 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-2 div.sk-item::before, #sk-container-id-2 div.sk-parallel-item::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-2 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-2 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-2 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-2 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-2 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-2 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-2 div.sk-label-container {text-align: center;}#sk-container-id-2 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-2 div.sk-text-repr-fallback {display: none;}</style><div id=\"sk-container-id-2\" class=\"sk-top-container\"><div class=\"sk-text-repr-fallback\"><pre>LinearRegression()</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class=\"sk-container\" hidden><div class=\"sk-item\"><div class=\"sk-estimator sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-2\" type=\"checkbox\" checked><label for=\"sk-estimator-id-2\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">LinearRegression</label><div class=\"sk-toggleable__content\"><pre>LinearRegression()</pre></div></div></div></div></div>"
            ]
          },
          "metadata": {},
          "execution_count": 14
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "7. Getting Model Coefficients"
      ],
      "metadata": {
        "id": "6M4xWQ8p_IYe"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "slope = model.coef_[0]\n",
        "\n",
        "intercept = model.intercept_\n",
        "\n",
        "print('Slope', slope)\n",
        "print('Intercept', intercept)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "k7FdodUb_I6V",
        "outputId": "c8652bb0-2bc7-4b5b-a0bb-3b6b9bc73416"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Slope [2.47297297]\n",
            "Intercept [82.48648649]\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **8. Visualizing the Linear Regression Line**"
      ],
      "metadata": {
        "id": "2AAmOKDQBQdC"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "plt.scatter(X,Y)\n",
        "plt.plot(X,model.predict(X), color='red')\n",
        "plt.xlabel('Independent Variable (X)')\n",
        "plt.ylabel('Dependent Variable (Y)')\n",
        "plt.title('Linear Regression')\n",
        "plt.show()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 472
        },
        "id": "r43i9LvzBQ4G",
        "outputId": "857cb5da-fb4b-4200-eb8c-e4ba826c990e"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **9. Making Predictions**"
      ],
      "metadata": {
        "id": "6xtFuc9GCgH4"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "input_value = np.array([[2]])\n",
        "predicted_Y = model.predict(input_value)\n",
        "\n",
        "print(predicted_Y)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "bxBKEg3hCgjI",
        "outputId": "07038675-bac0-4863-8f73-b91ed0463960"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "[[87.43243243]]\n"
          ]
        },
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.10/dist-packages/sklearn/base.py:439: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        }
      ]
    }
  ]
}loading L4_Simple_Linear_Regression.ipynb…]()


## Conclusion

- Summary of key points and importance in data science and project management.

## References

- List of sources and recommended readings.
